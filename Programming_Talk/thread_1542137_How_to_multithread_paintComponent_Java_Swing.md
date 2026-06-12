---
title: "How to multithread paintComponent Java Swing"
date: 2010-07-30
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-30
I am rendering a few charts and I would like to use threading to take advantage of my multiple cores to enhance performance.  I am trying to thread the paintComponent function of JFreeChart's ChartPanel.  I can get away with it because it renders the image as a buffered image.  So I think I only need to be careful about the calls g2 on the swing thread.  Here is the function:

[PHP]
   /**
     * Paints the component by drawing the chart to fill the entire component,
     * but allowing for the insets (which will be non-zero if a border has been
     * set for this component).  To increase performance (at the expense of
     * memory), an off-screen buffer image can be used.
     *
     * @param g  the graphics device for drawing on.
     */
    public void paintComponent(Graphics g) {
        super.paintComponent(g);
        if (this.chart == null) {
            return;
        }
        Graphics2D g2 = (Graphics2D) g.create();

        // first determine the size of the chart rendering area...
        Dimension size = getSize();
        Insets insets = getInsets();
        Rectangle2D available = new Rectangle2D.Double(insets.left, insets.top,
                size.getWidth() - insets.left - insets.right,
                size.getHeight() - insets.top - insets.bottom);

        // work out if scaling is required...
        boolean scale = false;
        double drawWidth = available.getWidth();
        double drawHeight = available.getHeight();
        this.scaleX = 1.0;
        this.scaleY = 1.0;

        if (drawWidth < this.minimumDrawWidth) {
            this.scaleX = drawWidth / this.minimumDrawWidth;
            drawWidth = this.minimumDrawWidth;
            scale = true;
        }
        else if (drawWidth > this.maximumDrawWidth) {
            this.scaleX = drawWidth / this.maximumDrawWidth;
            drawWidth = this.maximumDrawWidth;
            scale = true;
        }

        if (drawHeight < this.minimumDrawHeight) {
            this.scaleY = drawHeight / this.minimumDrawHeight;
            drawHeight = this.minimumDrawHeight;
            scale = true;
        }
        else if (drawHeight > this.maximumDrawHeight) {
            this.scaleY = drawHeight / this.maximumDrawHeight;
            drawHeight = this.maximumDrawHeight;
            scale = true;
        }

        Rectangle2D chartArea = new Rectangle2D.Double(0.0, 0.0, drawWidth,
                drawHeight);

        // are we using the chart buffer?
        if (this.useBuffer) {

            // do we need to resize the buffer?
            if ((this.chartBuffer == null)
                    || (this.chartBufferWidth != available.getWidth())
                    || (this.chartBufferHeight != available.getHeight())) {
                this.chartBufferWidth = (int) available.getWidth();
                this.chartBufferHeight = (int) available.getHeight();
                GraphicsConfiguration gc = g2.getDeviceConfiguration();
                this.chartBuffer = gc.createCompatibleImage(
                        this.chartBufferWidth, this.chartBufferHeight,
                        Transparency.TRANSLUCENT);
                this.refreshBuffer = true;
            }

            // do we need to redraw the buffer?
            if (this.refreshBuffer) {

                this.refreshBuffer = false; // clear the flag

                Rectangle2D bufferArea = new Rectangle2D.Double(
                        0, 0, this.chartBufferWidth, this.chartBufferHeight);

                Graphics2D bufferG2 = (Graphics2D)
                        this.chartBuffer.getGraphics();
                Rectangle r = new Rectangle(0, 0, this.chartBufferWidth,
                        this.chartBufferHeight);
                bufferG2.setPaint(getBackground());
                bufferG2.fill(r);
                if (scale) {
                    AffineTransform saved = bufferG2.getTransform();
                    AffineTransform st = AffineTransform.getScaleInstance(
                            this.scaleX, this.scaleY);
                    bufferG2.transform(st);
                    this.chart.draw(bufferG2, chartArea, this.anchor,
                            this.info);
                    bufferG2.setTransform(saved);
                }
                else {
                    this.chart.draw(bufferG2, bufferArea, this.anchor,
                            this.info);
                }

            }

            // zap the buffer onto the panel...
            g2.drawImage(this.chartBuffer, insets.left, insets.top, this);

        }

        // or redrawing the chart every time...
        else {

            AffineTransform saved = g2.getTransform();
            g2.translate(insets.left, insets.top);
            if (scale) {
                AffineTransform st = AffineTransform.getScaleInstance(
                        this.scaleX, this.scaleY);
                g2.transform(st);
            }
            this.chart.draw(g2, chartArea, this.anchor, this.info);
            g2.setTransform(saved);

        }

        Iterator iterator = this.overlays.iterator();
        while (iterator.hasNext()) {
            Overlay overlay = (Overlay) iterator.next();
            overlay.paintOverlay(g2, this);
        }

        // redraw the zoom rectangle (if present) - if useBuffer is false,
        // we use XOR so we can XOR the rectangle away again without redrawing
        // the chart
        drawZoomRectangle(g2, !this.useBuffer);

        g2.dispose();

        this.anchor = null;
        this.verticalTraceLine = null;
        this.horizontalTraceLine = null;

    }
[/PHP]

Here is my attempt to thread it:

[PHP]
[B]	public void paintComponent(Graphics g) 
	{
		final ChartPanel cpf = this;
		final Graphics gf = g;
		final Graphics2D g2 = (Graphics2D) g.create();
		final GraphicsConfiguration gc = g2.getDeviceConfiguration();
		
		initPanel(g);
		
		if(this.useBuffer)
		{
		new Thread(new Runnable() {
			public void run() {
				cpf.paintComponen(gf, gc, g2);
			}
		}).start();
		}
		else this.paintComponen(g, gc, g2);
	}
	
	public void initPanel(Graphics g)
	{
		super.paintComponent(g);
	}[/B]

	/**
	 * Paints the component by drawing the chart to fill the entire component,
	 * but allowing for the insets (which will be non-zero if a border has been
	 * set for this component).  To increase performance (at the expense of
	 * memory), an off-screen buffer image can be used.
	 *
	 * @param g  the graphics device for drawing on.
	 */
	public void paintComponen(Graphics g, GraphicsConfiguration gc, Graphics2D g2) {
		//super.paintComponent(gf);

		if (this.chart == null) {
			return;
		}
		// first determine the size of the chart rendering area...
		Dimension size = getSize();
		Insets insets = getInsets();
		Rectangle2D available = new Rectangle2D.Double(insets.left, insets.top,
				size.getWidth() - insets.left - insets.right,
				size.getHeight() - insets.top - insets.bottom);

		// work out if scaling is required...
		boolean scale = false;
		double drawWidth = available.getWidth();
		double drawHeight = available.getHeight();
		this.scaleX = 1.0;
		this.scaleY = 1.0;

		if (drawWidth < this.minimumDrawWidth) {
			this.scaleX = drawWidth / this.minimumDrawWidth;
			drawWidth = this.minimumDrawWidth;
			scale = true;
		}
		else if (drawWidth > this.maximumDrawWidth) {
			this.scaleX = drawWidth / this.maximumDrawWidth;
			drawWidth = this.maximumDrawWidth;
			scale = true;
		}

		if (drawHeight < this.minimumDrawHeight) {
			this.scaleY = drawHeight / this.minimumDrawHeight;
			drawHeight = this.minimumDrawHeight;
			scale = true;
		}
		else if (drawHeight > this.maximumDrawHeight) {
			this.scaleY = drawHeight / this.maximumDrawHeight;
			drawHeight = this.maximumDrawHeight;
			scale = true;
		}

		Rectangle2D chartArea = new Rectangle2D.Double(0.0, 0.0, drawWidth,
				drawHeight);

		// are we using the chart buffer?
				if (this.useBuffer) {

					// do we need to resize the buffer?
							if ((this.chartBuffer == null)
									|| (this.chartBufferWidth != available.getWidth())
									|| (this.chartBufferHeight != available.getHeight())) {
								this.chartBufferWidth = (int) available.getWidth();
								this.chartBufferHeight = (int) available.getHeight();
								this.chartBuffer = gc.createCompatibleImage(
										this.chartBufferWidth, this.chartBufferHeight,
										Transparency.TRANSLUCENT);
								this.refreshBuffer = true;
							}

							// do we need to redraw the buffer?
							if (this.refreshBuffer) {

								this.refreshBuffer = false; // clear the flag

								Rectangle2D bufferArea = new Rectangle2D.Double(
										0, 0, this.chartBufferWidth, this.chartBufferHeight);

								Graphics2D bufferG2 = (Graphics2D)
								this.chartBuffer.getGraphics();
								Rectangle r = new Rectangle(0, 0, this.chartBufferWidth,
										this.chartBufferHeight);
								bufferG2.setPaint(getBackground());
								bufferG2.fill(r);
								if (scale) {
									AffineTransform saved = bufferG2.getTransform();
									AffineTransform st = AffineTransform.getScaleInstance(
											this.scaleX, this.scaleY);
									bufferG2.transform(st);
									this.chart.draw(bufferG2, chartArea, this.anchor,
											this.info);
									bufferG2.setTransform(saved);
								}
								else {
									this.chart.draw(bufferG2, bufferArea, this.anchor,
											this.info);
								}

							}

							// zap the buffer onto the panel...
							final Graphics2D g2f = g2;
							final Image buffimgfin = this.chartBuffer;
							final Insets insetsf = insets;
							final ChartPanel thispanelfinal = this;
							
							try {
								[B]SwingUtilities.invokeAndWait(new Runnable() {
									public void run() {
										g2f.drawImage(buffimgfin, insetsf.left, insetsf.top, thispanelfinal);
									}
								});
							} catch (InterruptedException e) {
								// TODO Auto-generated catch block
								e.printStackTrace();
							} catch (InvocationTargetException e) {
								// TODO Auto-generated catch block
								e.printStackTrace();
							}[/B]

				}

				// or redrawing the chart every time...
				else {

					AffineTransform saved = g2.getTransform();
					g2.translate(insets.left, insets.top);
					if (scale) {
						AffineTransform st = AffineTransform.getScaleInstance(
								this.scaleX, this.scaleY);
						g2.transform(st);
					}
					this.chart.draw(g2, chartArea, this.anchor, this.info);
					g2.setTransform(saved);

				}

				Iterator iterator = this.overlays.iterator();
				while (iterator.hasNext()) {
					Overlay overlay = (Overlay) iterator.next();
					overlay.paintOverlay(g2, this);
				}

				// redraw the zoom rectangle (if present) - if useBuffer is false,
				// we use XOR so we can XOR the rectangle away again without redrawing
				// the chart
				drawZoomRectangle(g2, !this.useBuffer);

				g2.dispose();

				this.anchor = null;
				this.verticalTraceLine = null;
				this.horizontalTraceLine = null;

	}
[/PHP]

The part that I modified is surrounded by ** and **...was supposed to produce bold text.  However, when I run the application, the charts are blank.  I can resize, click on them without crashing / errors, but no charts are drawn.  Any idea what's wrong or the proper way to multi-thread the above function?

---

### Post by PaulM1985 on 2010-07-30
I think that I would use threads to create part of the chart and allow paintComponent to do that actual painting.

For example if paintComponent had to paint two images which where dynamically created, I would have something like

pseudocode:
```

paintComponent(Graphics g)
{
    Image1Creator im1 = new Image1Creator();
    Thread t1 = new Thread(im1);
    t1.start();

    Image2Creator im2 = new Image2Creator();
    Thread t2 = new Thread(im2);
    t2.start()
   
    t1.join();
    t2.join();

    g.Draw(im1.getImage());
    g.Draw(im2.getImage());
}

```

In this way the creation of your dynamic content is all done in the threads and you leave the drawing of your content to the paint method.  I think threading drawing (eg g.draw) is generally a bad idea (think I read it somewhere, not sure).  So this way you create your content in the threads and draw is done as normal.

Paul

---

### Post by SNYP40A1 on 2010-07-30
I agree, the image can be rendered in separate threads as a buffered image, but the actual drawing of the image to the screen needs to happen on the Swing thread.  So that's why I did this:

[PHP]
                            // zap the buffer onto the panel...
                            final Graphics2D g2f = g2;
                            final Image buffimgfin = this.chartBuffer;
                            final Insets insetsf = insets;
                            final ChartPanel thispanelfinal = this;
                            
                            try {
                                [B]SwingUtilities.invokeAndWait(new Runnable() {
                                    public void run() {
                                        g2f.drawImage(buffimgfin, insetsf.left, insetsf.top, thispanelfinal);
                                    }
                                });
                            } catch (InterruptedException e) {
                                // TODO Auto-generated catch block
                                e.printStackTrace();
                            } catch (InvocationTargetException e) {
                                // TODO Auto-generated catch block
                                e.printStackTrace();
                            }[/B]

[/PHP]

That puts the draw event in the Swing Queue to be rendered.  But I wonder if some event causes it not to render by being removed from the queue.  All I get is a blank gray canvas.  I can resize the canvas and the gray area resizes as well so I think the super.paintComponent(g) method is called, but it seems that the buffered image is not drawn.

---

### Post by SNYP40A1 on 2010-07-30
Update: I moved this post over to Java Ranch here:

[http://www.coderanch.com/t/504885/GUI/java/do-render-draw-buffered-Images#2278543](http://www.coderanch.com/t/504885/GUI/java/do-render-draw-buffered-Images#2278543)

Don't mean to cross-post, I just realized that this is a more advanced swing topic and should probably be asked in a Java Swing-specific forum.  If you want to respond, I can post your response over there so you don't have to sign up.

---

### Post by PaulM1985 on 2010-07-31
Is the drawImage being called?  Have you tried putting a print statement next to it?

Also, I mentioned in my previous post that the draw() stuff should be done in the paintComponent() method.  In your example it is being completed in the paintComponen() method, a method in a Runnable object that you have defined to run in a separate thread to the paintComponent().  This is in the lines:

```

        new Thread(new Runnable() {
            public void run() {
                cpf.paintComponen(gf, gc, g2); // This is being run on a 
                                               // separate thread and this
                                               // calls draw() functions
            }
        }).start(); 

```

Paul

---

### Post by SNYP40A1 on 2010-07-31
I think you're right about draw() stuff being done in paintComponent() method.  One paradigm for multi-threading image rendering would be to maintain an imageBuffer, as JfreeChart has done, and then also keep a flag which notes whether the buffer needs to be reconstructed/computed or simply redrawn (display the image to the screen).  If re-drawn, the paintComponent method could simply fire off a thread which recomputes the buffer and then the paintComponent thread simply returns after firing off the new thread.  The new thread renders the buffer and then calls repaint() so that the Swing Event Dispatch thread would again call paintComponent.  PaintComponent() then checks the buffer flag and sees that the buffer is up-to-date.  So the buffer is drawn to the screen using the Swing thread.  That's what I am trying to do, but it's not working right.  Although it does render and although I am using multiple threads, it's taking just as long and the graphics temporarily glitch during rendering.  I think it has something to do with not buffering the re-draw requests.  When a repaint() request comes in with a changed buffer, a new thread is simply started to recompute the imageBuffer.  While that is happening, if some property of the chart changes which causes the isBufferValid flag to flip to false, then on the next repaint request, another thread will be generated to repaint the buffer (while the previous thread might still be running).  As I mentioned earlier, I think Swing has some smart way of handling multiple repaint() requests for the same component().  If bufferedImages are rendered in an "offline thread" then, some logic needs to be put in place to handle multiple requests to re-render the same image...I think that's what might be happening.

> **PaulM1985 said:**
> Is the drawImage being called?  Have you tried putting a print statement next to it?

Also, I mentioned in my previous post that the draw() stuff should be done in the paintComponent() method.  In your example it is being completed in the paintComponen() method, a method in a Runnable object that you have defined to run in a separate thread to the paintComponent().  This is in the lines:

```

        new Thread(new Runnable() {
            public void run() {
                cpf.paintComponen(gf, gc, g2); // This is being run on a 
                                               // separate thread and this
                                               // calls draw() functions
            }
        }).start(); 

```

Paul

---

### Post by PaulM1985 on 2010-08-02
Are you making sure that on every call of repaint a thread is not started for recreating your chart?

What I mean is, paintComponent has been called, the chart needs recreating so you start up a thread to create it, then paintComponent is called again, you see that the chart needs recreating but you don't see that a thread is already working on it so you start off another to do it.  Try and avoid this.

Also, if you just have a thread creating an image, and the paintComponent waiting for it, it is going to take just as long to do because instead of creating the image in the main thread you are just doing it in another.  Ideally you would be using multiple threads to do multiple pieces of work, not just swapping the main thread for another.

Paul

---

