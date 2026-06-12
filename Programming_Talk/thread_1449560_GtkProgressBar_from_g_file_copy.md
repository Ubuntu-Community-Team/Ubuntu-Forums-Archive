---
title: "GtkProgressBar from g_file_copy"
date: 2010-04-08
forum: Programming Talk
---

### Post by Milliways on 2010-04-08
I have a program which can copy files - using the following:-

```
g_file_copy(source, destination,
    G_FILE_COPY_NOFOLLOW_SYMLINKS | G_FILE_COPY_OVERWRITE | G_FILE_COPY_ALL_METADATA,
    NULL,
    (GFileProgressCallback) transfer_progress_cb,
    progress,
    &error);

```
I would like to display a progress bar, and have the following function.

```
static void
transfer_progress_cb (goffset cur_bytes, goffset total_bytes, gpointer data)
{
    GtkProgressBar	*pbar = (GtkProgressBar *)data;
    if (cur_bytes > 0)
    {
	gdouble	val = (gfloat) cur_bytes / (gfloat) total_bytes;
	gtk_progress_bar_set_fraction(GTK_PROGRESS_BAR(pbar), val);
	g_debug("%f", val);
    }
}

```
Unfortunately, this does not display progress. (The code is being called as the debug messages indicate.)
The bar suddenly jumps from 0% to 100% at the end of the copy.

I suspect this is because the g_file_copy is blocking the thread.
I have tried all sorts of tricks to force display updating, without success.

I have considered using g_file_copy_async, but as the copy is deeply embedded in a number of loops, this would not be easy.

The progress_callback in g_file_copy would seem to be of limited use.
I am sure what I want to do is not uncommon, but cannot find any examples.

All the GtkProgressBar examples I have seen use a timer.

Can anyone suggest a way to display progress - and hopefully an example.

---

