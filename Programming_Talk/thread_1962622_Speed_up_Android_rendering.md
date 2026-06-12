---
title: "Speed up Android rendering"
date: 2012-04-21
forum: Programming Talk
---

### Post by PaulM1985 on 2012-04-21
Hi

I have been writing a game for Android and I have been trying to work out how to get more frames per second.  Most of the time seems to be spent rendering (30ms) compared to updating the state of the game (8ms).

Below is the code for rendering:
```


    static private Map<GameRenderIds, Bitmap> sDrawingImages;

    public void render()
    {
    	this.postInvalidate();
    }
    
    public void onDraw(Canvas canvas) 
    {
	super.onDraw(canvas);

	Date startRender = new Date();
		
        // Don't paint if we have nothing to paint
        if (mGame == null)
        {
            return;
        }

        if (mGame.exitConditionMet())
        {
            canvas.drawBitmap(sGameOver, null, new Rect(0, 0, getWidth(), getHeight()), mPaint);
            return;
        }
        
        // Remember, all things in the game are defined as bottom left.
        // Get the bottom left corner of the screen

        int height = this.getHeight();

        canvas.drawBitmap(sBackBackground, null, new Rect(0, 0, getWidth(), getHeight()), mPaint);
        
        Rectangle2D gameWindow = mGame.getGameWindow();

        Rect screenWindow = new Rect(0, 0, getWidth(), getHeight());
        
        List<DrawingEntity> drawingEntities = mGame.getDrawList();
        for (DrawingEntity ent : drawingEntities)
        {
            CoordConverter convertCat = new CoordConverter(gameWindow, ent.Rect, height);
            int drawingCoordsX = convertCat.drawingCoordsX;
            int drawingCoordsY = convertCat.drawingCoordsY;
            int drawingCoordsWidth = convertCat.drawingCoordsWidth;
            int drawingCoordsHeight = convertCat.drawingCoordsHeight;
        	Rect dst = new Rect(drawingCoordsX, drawingCoordsY,
        			drawingCoordsX + drawingCoordsWidth,
        			drawingCoordsY + drawingCoordsHeight);
        	
        	Rect temp1 = new Rect(screenWindow);
        	Rect temp2 = new Rect(screenWindow);
        	if (temp1.contains(dst) || temp2.intersects(dst.left, dst.top, dst.right, dst.bottom))
        	{
	            Bitmap img = getImage(ent.Id);
	            Rect src = new Rect(0, 0, img.getWidth(), img.getHeight());
	            canvas.drawBitmap(img, src, dst, mPaint);
        	}	
        }

        // Add text to the info template
        PlayableCharacter player = mGame.getPlayableCharacter();
        String grenadesRemaining = "Grenades: " + player.getGrenadesRemaining();
        int playerAmmo = player.getAmmoRemaining();
        String bulletsRemaining;
        if (playerAmmo != -1)
        {
            bulletsRemaining = "Bullets: " + playerAmmo;
        }
        else
        {
            bulletsRemaining = "Bullets: Unlimited";
        }
        String health = "Health: " + player.getHealth();

        canvas.drawText(bulletsRemaining, 300, 25, mPaint);
        canvas.drawText(grenadesRemaining, 300, 35, mPaint);
        canvas.drawText(health, 300, 45, mPaint);
        
        // Debug info
        sFrames++;
        
        // Draw frames per second
        Date newTime = new Date();
        long timeBetweenFrames = newTime.getTime() - sTimeOfLastFrame.getTime(); 
        double fps = 1000 / timeBetweenFrames;
        canvas.drawText("fps: " + fps, 10, 25, mPaint);
        sTimeOfLastFrame = newTime;
        
        // Draw time taken to render
        long renderTime = newTime.getTime() - startRender.getTime();
        sCumRenderTime += renderTime;
        canvas.drawText("Render time " + renderTime + " " + sCumRenderTime/sFrames, 10, 35, mPaint);

        // Time processing game
        long gameProcessTime = timeBetweenFrames - renderTime; 
        sCumProcessTime += gameProcessTime;
        canvas.drawText("Game process time " + gameProcessTime + " " + sCumProcessTime/sFrames, 10, 45, mPaint);
    }

    private Bitmap getImage(GameRenderIds id)
    {
    	if (sDrawingImages == null)
    	{
    		sDrawingImages = new HashMap<GameRenderIds, Bitmap>();
    	}
    	
    	if (!sDrawingImages.containsKey(id))
    	{
    		Bitmap image = loadImage(id);
    		sDrawingImages.put(id, image);
    	}
    	
    	return sDrawingImages.get(id);
    }
    
    private Bitmap loadImage(GameRenderIds id)
    {		
		switch (id)
		{
		case SOME_CASE:
			return BitmapFactory.decodeResource(getResources(), R.drawable.some_resource);

```

I am running this on a Sony Xperia Play, so I expected to have very high performance since the phone is designed for gaming.  I found the canvas.drawBitmap() functions on the android API and assumed that this is what I would need to do to render my game objects, is this correct?

Since I am only getting around 25 fps on Sony Xperia Play, I would expect it to run very slowly on some other phones.

Any advice would be much appreciated.

Paul

---

### Post by gardnan on 2012-04-21
Sorry, but I don't know much about Android development, but, I have heard that the standard profiler for the Android platform is Traceview.

If you have never used a profiler before, basically it is a tool that allows you to track exactly which of your methods are sucking up any extra CPU time, so you can tune them to be more efficient.

From the documentation, it looks like to use it you include the class 'Debug' and then call [PHP]Debug.startMethodTracing("sectionname");
...
Debug.stopMethodTracing();[/PHP]For more information:

[http://developer.android.com/guide/developing/debugging/debugging-tracing.html](http://developer.android.com/guide/developing/debugging/debugging-tracing.html)

---

### Post by Bachstelze on 2012-04-21
Don't do it all in Java. Use the NDK and JNI.

---

### Post by fct on 2012-04-23
The Canvas class is not the fastest API to use for 2D games, but should suffice for simple ones.

If you want more FPS, then you have to make use of GPU acceleration. Canvas only supports hardware acceleration from Android 3.0 on, and restricted to certain methods.

It's better to use OpenGL ES:

[http://developer.android.com/guide/topics/graphics/opengl.html](http://developer.android.com/guide/topics/graphics/opengl.html)

If you want to save yourself time and lines of code, just use a game engine that takes care of the OpenGL low-level access. AndEngine and libGDX are popular choices:

[http://www.andengine.org/](http://www.andengine.org/)

[http://code.google.com/p/libgdx/](http://code.google.com/p/libgdx/)

---

### Post by 11jmb on 2012-04-23
> **Bachstelze said:**
> Don't do it all in Java. Use the NDK and JNI.

+1

I also recommend doing some good profiling, so that you can figure out which functions in your call graph are the "low-hanging fruit" that you can re-implement with C/NDK. 

This profiling stage will allow you to optimize critical sections, while saving your time, because you don't have to waste your time re-implementing everything


Also, which android version are you developing towards? newer versions have hardware acceleration for rendering implemented.

---

