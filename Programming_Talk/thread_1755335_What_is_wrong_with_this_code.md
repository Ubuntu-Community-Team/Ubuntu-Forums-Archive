---
title: "What is wrong with this code?"
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

### Post by myrtle1908 on 2011-05-11
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

What have you tried?

You assume those reading your post are clairvoyant yes?  We are not.  Moreover, you suggest we interpret this code without some semblance of context?  Brilliant.

This forum won't do your job/homework for you.

I suggest that you are the "error" which needs resolving.

---

### Post by zobayer1 on 2011-05-11
What were your errors, and what did you expect?

---

### Post by etdsbastar on 2011-05-11
> **myrtle1908 said:**
> What have you tried?

You assume those reading your post are clairvoyant yes?  We are not.  Moreover, you suggest we interpret this code without some semblance of context?  Brilliant.

This forum won't do your job/homework for you.

I suggest that you are the "error" which needs resolving.

Hey myrtie,

If u want to help then help, please dont say cheap words to other forum members. When you registered in this form, you have signed a code of conduct, remember that. This forum is running because we are helping each other, else this would have been closed a long time ago.

Don't ever help anyone if you have such aspects in mind.

Take care.

---

### Post by simeon87 on 2011-05-11
> **etdsbastar said:**
> Hey myrtie,

If u want to help then help, please dont say cheap words to other forum members. When you registered in this form, you have signed a code of conduct, remember that. This forum is running because we are helping each other, else this would have been closed a long time ago.

Don't ever help anyone if you have such aspects in mind.

Take care.

The question still stands though: what is wrong with the code? Posting a piece of code and expecting others to debug it is frowned upon, in particular when people post very long pieces of code. You have to tell the reader what the problem is.

- Is it not drawing at all?
- Is it not drawing a sine but some weird shape?

In your case, the code is pretty straightforward but I wouldn't know what to reply to help.

---

### Post by etdsbastar on 2011-05-11
> **zobayer1 said:**
> What were your errors, and what did you expect?

Dear Zobayer,

I am getting errors in this line:
```

protected override void DoPage(Graphics grfx, Color clr, int cx, int cy)
```

This line is not initialized by and giving DoPage delegate error.

Please help.

---

### Post by 102jon on 2011-05-11
lol. Please copy and paste the error message.

---

### Post by doas777 on 2011-05-11
change "overrides" to "virtual", or remove the token entirely. 
there is no overridable (or otherwise) member called "DoPage" in System.Windows.Forms.Forms

[http://msdn.microsoft.com/en-us/library/system.windows.forms.form.aspx](http://msdn.microsoft.com/en-us/library/system.windows.forms.form.aspx)

---

### Post by etdsbastar on 2011-05-11
> **doas777 said:**
> change "overrides" to "virtual", or remove the token entirely. 
there is no overridable (or otherwise) member called "DoPage" in System.Windows.Forms.Forms

[http://msdn.microsoft.com/en-us/library/system.windows.forms.form.aspx](http://msdn.microsoft.com/en-us/library/system.windows.forms.form.aspx)


Thanks doas,

The link helped me a lot. Solved the problem. Thank you all of you.

---

### Post by cgroza on 2011-05-11
> **etdsbastar said:**
> Thanks doas,

The link helped me a lot. Solved the problem. Thank you all of you.
You were lucky. You provided almost 0 information and still got help.
Your problem would have been solved much quicker if you would had given more information.
Next time, provide the needed information if you want quality help.

---

### Post by myrtle1908 on 2011-05-12
> **etdsbastar said:**
> Hey myrtie,

If u want to help then help, please dont say cheap words to other forum members. When you registered in this form, you have signed a code of conduct, remember that. This forum is running because we are helping each other, else this would have been closed a long time ago.

Don't ever help anyone if you have such aspects in mind.

Take care.

Rubbish. Show me where I violated the code of conduct.  If anything it is you who violated said terms - with your blatant "do my work for me" style post.  I'm more than happy to help - if only you had first helped yourself some.  I was pointing this out.  In hindsight I did so in a less than professional manner.

In my 400 odd posts here I have done nothing but help others.

Good luck to you.

---

### Post by doas777 on 2011-05-12
well, that is sufficient acrimony methinks.

<constructive criticism>
@Op: next time, first try at the [MSDN forums]("http://social.msdn.microsoft.com/Forums/en-US/category/visualbasic"). I hang out there too, and they are much better prepared for isolating issues and providing guidance on .Net development considerations. 

Additionally, when you encounter an error, please indicated in your OP post what line of the code the error occures on, and what the full text of the error message is. 

just some hints to help you get a better support experience.
</constructive criticism>

Cheers

---

### Post by etdsbastar on 2011-05-14
> **cgroza said:**
> You were lucky. You provided almost 0 information and still got help.
Your problem would have been solved much quicker if you would had given more information.
Next time, provide the needed information if you want quality help.

Thanks cgroza,

Sorry for the inconvenience caused to you all for lesser information. Next time, I will keep all this in mind. Sure.

---

