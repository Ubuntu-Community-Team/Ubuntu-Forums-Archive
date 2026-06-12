---
title: "What is wrong with this C# code?"
date: 2011-05-11
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-11
Hello there,

Please help to resolve error in this code:

```
using System;
using System.Drawing;
using System.Windows.Forms;

class SineCurve : Form
{
    public static void main ()
    {
        Application.Run (new SineCurve ());
    }
    
    public SineCurve ()
    {
        Text = "Sine Curve";
    }
    
    protected override void DoPage (Graphics grfx, Color clr, int cx, int cy)
    {
        PointF[] aptf = new PointF[cx];
        
        for (int i = 0; i < cx; i++)
        {
            aptf[i].X = i;
            aptf[i].Y = cy/2*(1-(float)Math.Sin(i*2*Math.pi/(cx-1)));
        }
        grfx.DrawLines(new Pen(clr),aptf);
    }
}
```

---

### Post by Arndt on 2011-05-11
> **etdsbastar said:**
> Hello there,

Please help to resolve error in this code:

```
using System;
using System.Drawing;
using System.Windows.Forms;

class SineCurve : Form
{
    public static void main ()
    {
        Application.Run (new SineCurve ());
    }
    
    public SineCurve ()
    {
        Text = "Sine Curve";
    }
    
    protected override void DoPage (Graphics grfx, Color clr, int cx, int cy)
    {
        PointF[] aptf = new PointF[cx];
        
        for (int i = 0; i < cx; i++)
        {
            aptf[i].X = i;
            aptf[i].Y = cy/2*(1-(float)Math.Sin(i*2*Math.pi/(cx-1)));
        }
        grfx.DrawLines(new Pen(clr),aptf);
    }
}
```

What's the error?

---

### Post by etdsbastar on 2011-05-11
> **Arndt said:**
> What's the error?

There is some delegate error in 
```

protected override DoPage...

```

Please do help... I am new to C#

---

### Post by Arndt on 2011-05-11
> **etdsbastar said:**
> There is some delegate error in 
```

protected override DoPage...

```

Please do help... I am new to C#

Is it not possible to show the whole and exact error message?

Besides, it's best if you close one of your threads about this - you have two now. Otherwise people will keep commenting in both.

---

