---
title: "C# - Crash when repainting on a subclass of panel"
date: 2009-10-23
forum: Programming Talk
---

### Post by PaulM1985 on 2009-10-23
Hi

I have a class which extends System.Windows.Forms.Panel called DrawArea which I am using to draw lines on.  The function I am using to draw the lines (reDraw()) is being run in a thread:

```

					// Create a new thread and start

calculate = new Thread(new ThreadStart(pictureBox1.reDraw));

calculate.Start();

```

so the user is able to click a button on the user interface to start and stop the animation. When I am drawing the lines, I am using the following code:

```

public void reDraw()

		{

			int i = 0;

			while (true)

			{

				if (i == 10)

				{

					i = 1;

					Thread.Sleep(1);

				}



				if (modeller != null)

				{

					this.Invalidate();

					modeller.calcNext();

				}



				i++;

			}
```

The overriden OnPaint method is:
```

protected override void OnPaint(PaintEventArgs paintEvnt)

		{

			double centre_x = this.Size.Width / 2.0;

			double centre_y = this.Size.Height / 4.0;

			double scale;

			Pen myPen = new Pen(System.Drawing.Color.Red);

			Graphics formGraphics = paintEvnt.Graphics;



			if (modeller != null)

			{

				Array objects = modeller.getObjects().ToArray();

				String time = modeller.getTime().ToString();

				PendulumModel.Model.Object upperObject = (PendulumModel.Model.Object)objects.GetValue(0);

				PendulumModel.Model.Object lowerObject;



							// Change time to 1 decimal place

				time = time.Substring(0, time.IndexOf(".") + 2);



							// Calculate the drawing scale

				scale = modeller.getTotalCableLength() / (this.Height / 2.0);



							// Draw line to first object

				formGraphics.DrawLine(myPen, (int)centre_x,

					(int)centre_y,

					(int)(centre_x + upperObject.getPosition().getX() / scale),

					(int)(centre_y - upperObject.getPosition().getY() / scale));



							// Loop over the remainder of

							// the objects and draw connections

				for (int i = 1; i < objects.Length; i++)

				{

					lowerObject = (PendulumModel.Model.Object) objects.GetValue(i);

					formGraphics.DrawLine(myPen,

						(int)(centre_x + upperObject.getPosition().getX() / scale),

						(int)(centre_y - upperObject.getPosition().getY() / scale),

						(int)(centre_x + lowerObject.getPosition().getX() / scale),

						(int)(centre_y - lowerObject.getPosition().getY() / scale));



					upperObject = lowerObject;

				}



				formGraphics.DrawString("Time = " + time,

					new System.Drawing.Font("Arial", 10),

					new System.Drawing.SolidBrush(System.Drawing.Color.Red),

					new System.Drawing.PointF(10, this.Height - 40));

			}



			myPen.Dispose();

			formGraphics.Dispose();

		}
```

The error I get when it crashes is shown below:

Unhandled Exception: System.InvalidOperationException: List has changed.
  at System.Collections.ArrayList+SimpleEnumerator.MoveNext () [0x00000] 
  at System.Windows.Forms.Hwnd.AddInvalidArea (Rectangle rect) [0x00000] 
  at System.Windows.Forms.Hwnd.AddInvalidArea (Int32 x, Int32 y, Int32 width, Int32 height) [0x00000] 
  at System.Windows.Forms.XplatUIX11.AddExpose (System.Windows.Forms.Hwnd hwnd, Boolean client, Int32 x, Int32 y, Int32 width, Int32 height) [0x00000] 
  at System.Windows.Forms.XplatUIX11.Invalidate (IntPtr handle, Rectangle rc, Boolean clear) [0x00000] 
  at System.Windows.Forms.XplatUI.Invalidate (IntPtr handle, Rectangle rc, Boolean clear) [0x00000] 
  at System.Windows.Forms.Control.Invalidate (Rectangle rc, Boolean invalidateChildren) [0x00000] 
  at System.Windows.Forms.Control.Invalidate () [0x00000] 
  at Pendulum.DrawArea.reDraw () [0x00000] 

I guess the problem is when I call this.invalidate in the reDraw method.  (It doesn't crash straight away, the time when it crashes varies.)

I had a look at the Panel class information at:
[http://msdn.microsoft.com/en-us/library/system.windows.forms.panel.aspx](http://msdn.microsoft.com/en-us/library/system.windows.forms.panel.aspx)

and found the following:
"Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe."

Does this mean that the problem is because I am using threading for the redraw()?  Do I have to make it a "static member"?  If so, how is this done?

Or have I missed the problem and it is something else?

Thanks for any advice

Paul

---

### Post by PaulM1985 on 2009-10-23
Also, I don't seem to get this problem when opening and running my project in Visual Studio in Windows.

Does C# not work on Linux?  It creates .exe files so are they built for Windows and is this a bug in Mono rather than in my program?

Paul

---

### Post by PaulM1985 on 2009-10-23
Ok.  After a night of trying to get stuff working..

The problem I initially reported is on my desktop PC. (64 bit).  I have copied by compiled code from Visual Studio in windows onto my laptop (32 bit) and that will run ok when I use: mono Pendulum.exe.  However, I am not able to compile my code on my laptop getting this error:

[Task:File=/home/paul/Desktop/Pendulum/Pendulum/Form1.resx, Line=0, Column=0, Type=Error, Priority=Normal, Description=ApplicationName='resgen2', CommandLine='/compile "/home/paul/Desktop/Pendulum/Pendulum/Form1.resx"', CurrentDirectory='/home/paul/Desktop/Pendulum/Pendulum', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games']

I have had a look at my csharp language bindings on my laptop and they are version 1.0.0, the ones on my desktop are 2.0.0.

Does anyone know how I can update these, or just get at least one of the versions working?

Paul

---

### Post by directhex on 2009-10-24
> **PaulM1985 said:**
> Ok.  After a night of trying to get stuff working..

The problem I initially reported is on my desktop PC. (64 bit).  I have copied by compiled code from Visual Studio in windows onto my laptop (32 bit) and that will run ok when I use: mono Pendulum.exe.  However, I am not able to compile my code on my laptop getting this error:

[Task:File=/home/paul/Desktop/Pendulum/Pendulum/Form1.resx, Line=0, Column=0, Type=Error, Priority=Normal, Description=ApplicationName='resgen2', CommandLine='/compile "/home/paul/Desktop/Pendulum/Pendulum/Form1.resx"', CurrentDirectory='/home/paul/Desktop/Pendulum/Pendulum', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games']

I have had a look at my csharp language bindings on my laptop and they are version 1.0.0, the ones on my desktop are 2.0.0.

Does anyone know how I can update these, or just get at least one of the versions working?

Paul

Off the top of my head, i'd say you're missing packages you need such as the one with resgen2 in it. Which Ubuntu release are you on? The package names vary between releases

---

### Post by PaulM1985 on 2009-10-24
My desktop is Jaunty and my laptop is Hardy.

Paul

---

### Post by directhex on 2009-10-24
> **PaulM1985 said:**
> My desktop is Jaunty and my laptop is Hardy.

Paul

for both Jaunty and Hardy, you need the package mono-2.0-devel for resgen2

However, Mono in Hardy is antique

---

### Post by PaulM1985 on 2009-10-25
Thanks after doing that it is now running on my laptop.

Not sure what the problem is with my desktop, but at least I can have it running on one of them.  Thanks again.

Paul

---

