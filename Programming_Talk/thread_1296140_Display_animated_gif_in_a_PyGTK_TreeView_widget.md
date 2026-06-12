---
title: "Display animated gif in a PyGTK TreeView widget"
date: 2009-10-20
forum: Programming Talk
---

### Post by Twiggy794 on 2009-10-20
I have a TreeView that I'm displaying in my application, and on load up, a job is run on each item in that TreeView.  While the job is running, I would like to display a spinner graphic (gif) in the "Status" column, and then once the job is completed, swap out the spinner with an icon showing success/failure depending on how the job turned out.

It looks like a gtk.CellRendererPixbuf() will only render the first frame of animation for a gif, and I can't see to find any existing API that will allow you to add a gtk.gdk.PixbufAnimation to a TreeView.  Is there a way that I'm not seeing?  Can anybody point me in the right direction?

Thanks!

---

### Post by Can+~ on 2009-10-20
Never tried that, but you could use a ProgressBar instead.

---

