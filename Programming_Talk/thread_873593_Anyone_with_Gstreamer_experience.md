---
title: "Anyone with Gstreamer experience?"
date: 2008-07-29
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-07-29
I am experimenting with gtkmm and gstreamer(and mixing C with C++ as a result :( ). I'll try to be as specific as I can:
1.As you know you can create a bus where gstreamer posts messages about the pipeline/media you created the bus for. ([more details here](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-bus.html#section-bus-howto))

2.I use the second method to connect to end-of-stream message:
  "g_signal_connect (bus, "message::eos", G_CALLBACK (cb_message_eos), NULL);"

3.And the callback just seeks to the beginning of the stream/media.

**But here's the problem:** callback(the seek function) fails with this error in the console--->** gst_element_seek: assertion `GST_IS_ELEMENT (element)' failed**

But there's something weird going on: If I put the same code in a button callback and click the button MYSELF after the stream/media has finished playing(after eos) then everything works perfectly.

Why is this happening?

---

### Post by kknd on 2008-07-29
How are you doing your "main loop"?

---

### Post by SledgeHammer_999 on 2008-07-29
Well I haven't implementing something specific to Gstreamer. I have the "default" Gtkmm uses (Gmainloop?).

(I can post the code if you want but it is a little messy)

---

### Post by kknd on 2008-07-29
Can you can paste it in [http://pastebin.com/](http://pastebin.com/) ?

---

### Post by SledgeHammer_999 on 2008-07-29
I didn't figure how to obtain a link to the posted thing in pastebin so I am providing a tarball :D

1.It can play only ogg files
2.Don't mind the weird numbers in the label. Just "Open..." and "Play".
3.Run it from a terminal so you can see the errors

Thanks for your efford.

---

### Post by kknd on 2008-07-29
Your callback for the bus messgae is wrong.

Your callback:

void main_window::end_file(main_window *data)

Should be :

void main_window::end_file(GstBus *bus, GstMessage *message, main_window* data)


Its working here. (You where using a GstBus as if it were your main_window*, I don't know why it didn't crashed there)

---

### Post by SledgeHammer_999 on 2008-07-29
hahahaha oops :) (although the doc wasn't clear enough for a noob like me)

THANK YOU.

---

