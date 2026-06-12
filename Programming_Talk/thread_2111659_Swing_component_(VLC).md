---
title: "Swing component (VLC)?"
date: 2013-02-02
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-02-02
Hi

I'm making an mp3 player using Java.
I'm almost done, I'm stuck with the GUI.

Check this picture out [http://www.pasteall.org/pic/44796](http://www.pasteall.org/pic/44796)

I need to know what is the highlighted section called in Swing if it's there?

Regards

---

### Post by ofnuts on 2013-02-02
> **3v3rgr33n said:**
> Hi

I'm making an mp3 player using Java.
I'm almost done, I'm stuck with the GUI.

Check this picture out [http://www.pasteall.org/pic/44796](http://www.pasteall.org/pic/44796)

I need to know what is the highlighted section called in Swing if it's there?

RegardsI don't really understand the question... are you taking about the VLC icon? or the window where it is displayed?

---

### Post by 3v3rgr33n on 2013-02-03
Yup!

I'm referring to the window the icon is displayed.

---

### Post by ofnuts on 2013-02-04
> **3v3rgr33n said:**
> Yup!

I'm referring to the window the icon is displayed.
I would  suppose some derived class of JComponent, or are you looking for a ready-made video widget?

---

### Post by Zugzwang on 2013-02-04
@OP: There are a couple of ways of "putting images into the UI" in Swing. If your image stays the same all the time or has only infrequent changes (like logos), then add it as an icon to a JLabel. The JLabel can then have an empty string as actual label.

If the content of the image changes dynamically, then typically you derive a JPanel and add customized painting code.

For both of these cases there should be examples in the Java Tutorial. If you can't find them, answer that here, and I'll see if I can find them.

If you are actually displaying a video, then there is probably a specialized Swing Component in some library that you can use. Bit since you said "MP3", you probably don't need this.

---

### Post by 3v3rgr33n on 2013-02-05
> **Zugzwang said:**
> @OP: There are a couple of ways of "putting images into the UI" in Swing. If your image stays the same all the time or has only infrequent changes (like logos), then add it as an icon to a JLabel. The JLabel can then have an empty string as actual label.

If the content of the image changes dynamically, then typically you derive a JPanel and add customized painting code.

For both of these cases there should be examples in the Java Tutorial. If you can't find them, answer that here, and I'll see if I can find them.

If you are actually displaying a video, then there is probably a specialized Swing Component in some library that you can use. Bit since you said "MP3", you probably don't need this.

I want to place the album artwork, so I guess it's going to change frequently.

Can I not use a Canvas instead?[B]

EDIT[/B]

I do not really need a video widget. I just need to place the album cover (if it's available from the mp3)

---

### Post by Zugzwang on 2013-02-05
> **3v3rgr33n said:**
> 
Can I not use a Canvas instead?


You shouldn't, as the old AWT widgets and Swing widgets shall not be mixed.

However, the only thing that you have to do is to override one method of the JPanel, just like you would do it a Canvas, so there is not really much of a difference.

You could still use a JLabel, though. Your album artwork won't change multiple times per second, so it's suitable.

---

### Post by 3v3rgr33n on 2013-02-05
JLabel it is then, thanks!

---

