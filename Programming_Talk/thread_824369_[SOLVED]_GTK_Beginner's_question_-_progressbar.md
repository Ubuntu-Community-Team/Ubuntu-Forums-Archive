---
title: "[SOLVED] GTK Beginner's question - progressbar"
date: 2008-06-10
forum: Programming Talk
---

### Post by anewguy on 2008-06-10
I have another beginner GTK question:

I have a progressbar defined and showing on the screen.  It is defined as a global.  I am trying to compute the % and update the progressbar, but instead no bars ever show on the progress bar.  Here's the code that tries to update the progressbar:

	     dwe_sofar = ((int)size_count % 1024);
             if (dwe_sofar == 0)
             {
                  dwe_percent = dwe_sofar / flash_size;
                  gtk_progress_bar_set_fraction (GTK_PROGRESS_BAR (progressbar1), 
		                                (gfloat)dwe_percent);
                  while (gtk_events_pending ()) gtk_main_iteration();


Basically I don't want to update the progressbar everytime I go through the parent routine, so I added this to try to force an update only when the number of bytes processed by the routine is a multiple of 1K.  If there is a problem in the parent routine a message box is used and at the time of it's display there is suddenly progress in the progressbar.

Being the first time I have tried to use this, I'm sure I'm doing something as dumb as dirt.

Any help would be greaty appreciated!!  :)

---

### Post by anewguy on 2008-06-10
Never mind - I really messed up trying to calc the percentage.

---

