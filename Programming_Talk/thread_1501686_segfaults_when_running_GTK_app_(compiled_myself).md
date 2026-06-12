---
title: "segfaults when running GTK app (compiled myself)"
date: 2010-06-04
forum: Programming Talk
---

### Post by jpka on 2010-06-04
Hi!
I'm trying to bugfix and enhance existing app, it's gtkterm 0.99.5 (serial/RS232 terminal) and it's in Ubuntu's repos. But it's seems not updated since 2005 :(
I get it here [http://www.jls-info.com/julien/linux/gtkterm-0.99.5.tar.gz](http://www.jls-info.com/julien/linux/gtkterm-0.99.5.tar.gz) then compile as is.
It work on rs232 receive, but when i try to 'Transmit hex data' it always segfaults, while original existing binary in my system, works good.
I'm too novice and can't imagine what can I do with segfaults and tons of trace output... Can you help me please?
PS. The result is same when I compile it in Eclipse IDE, or via commandline.
Thanks!:)

---

### Post by dwhitney67 on 2010-06-04
Please post the code that you modified, and any relevant information, such as data structures, typedefs, etc.

---

### Post by jpka on 2010-06-05
I'm **not** modified the code, just try to compile as is.
/home/distrib/gtkterm-0.99.5-orig$ ./configure 
make clean
make
src/gtkterm (program starts)
menu View-Send hexadecimal data (bottom frame appears)
Place cursor on text entry and...
1) press Enter:
- quitting with 'Segmentation fault'
2) type 00 and press Enter:
- quitting with 'Segmentation fault' and lots of output:
*** buffer overflow detected ***: src/gtkterm terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb6f80ef8]
/lib/tls/i686/cmov/libc.so.6[0xb6f7f000]
/lib/tls/i686/cmov/libc.so.6[0xb6f7e6f8]
etc.... (i attach txt file with it)

program compiles with warnings, most of it is:

[I]warning: pointer targets in passing argument 1 of ‘bla bla’ differ in signedness
[/I]
Sorry I don't know what mean 'typedefs', but if i try to modify code and comment out full body of this function, errors disappear (functionality also):

[SIZE="-2"]
[FONT="Courier New"]
gboolean Send_Hexadecimal(GtkWidget *widget, GdkEventKey *event, gpointer pointer)
{
  gint i;
  gchar *text, *current;
  gchar *message;
  guchar val;
  guint val_read;
  guint sent = 0;
  gchar written[3];
  gchar *all_written;


  text = (gchar *)gtk_entry_get_text(GTK_ENTRY(widget));

  all_written = g_malloc(strlen(text) * 2);
  all_written[0] = 0;
  current = text;
  i = 0;
  while(i < strlen(text))
    {
      if(sscanf(current, "%02X", &val_read) == 1)
	{
	  val = (guchar)val_read;
 	  send_serial(&val, 1);
	  sprintf(written, "%02X ", val);
	  strcat(all_written, written);
	  sent++;
	}
      while(i < strlen(text) && text[i] != ';' && text[i] != ' ')
	i++;
      if(text[i] == ';' || text[i] == ' ')
	{
	  i++;
	  current = &text[i];
	}
    }

  all_written[strlen(all_written) - 1] = 0;
  message = g_strdup_printf(_("\"%s\" : %d byte(s) sent !"), all_written, sent);
  Put_temp_message(message, 1500);
//  gtk_entry_set_text(GTK_ENTRY(widget), "");
  g_free(message);
  g_free(all_written);

  return FALSE;
}
[/FONT]
[/SIZE]

Thanks!

---

