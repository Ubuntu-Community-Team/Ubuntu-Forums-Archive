---
title: "Gtk Widget Transparency / Opacity"
date: 2012-05-06
forum: Programming Talk
---

### Post by jeff.biggeek02 on 2012-05-06
Hello,

I want to control the transparency of any given GTK widget (such as a button or text box) so that I can overlay them on a GtkImage Pixbuf.

I have tried the following, but my GdkWindow is null.

[System.ComponentModel.ToolboxItem(true)]
	public partial class MarkDownEditor : Gtk.Bin
	{
		public MarkDownEditor (IHostRequest hostRequest)
		{
			this.hostRequest = hostRequest;
			this.Build ();
			
			this.ShowAll();
			//ATTEMPT 1 - didn't work either
			//Cairo.Context cxt = Gdk.CairoHelper.Create(this.GdkWindow);
			//cxt.SetSourceRGBA(0.5, 0.5, 0.5, 0.0);
			//cxt.Paint();
			//cxt.Target.Dispose();
			//((IDisposable)cxt).Dispose();

			//ATTEMPT 2 - GdkWindow is null		
			this.GdkWindow.Opacity = 0.5;
		}
	}

Any suggestions on other approaches?  This is a custom widget of sorts that I'm adding to a plain old GtkWindow whenever this constructor is called.

---

