---
title: "Desktop disappeared"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by emreergecen on 2012-05-31
Hi everyone,

I have been learning to use Xubuntu for three months. Everything went fine until today. All of a sudden every icon on my desktop disappeared and I don' t know why. When I use terminal, I can reach the files on the desktop and when I use thunar, I can also access the files on the desktop. Help me! :D

Thanks

---

### Post by arubislander on 2012-05-31
You probably inadvertently set the desktop icons to be invisible.

Go to this path: Applications » Settings » Desktop. In Desktop preferences, go to 'Icons' tab. There, you just need to set 'Icon type' to 'None' and set it back to 'File/Launcher Icons' to bring them back.

I found this solution [here]("http://bayu.freelancer.web.id/2009/08/19/showhide-desktop-icons-in-xfce/")

---

### Post by emreergecen on 2012-05-31
Actually it did not work :(

---

### Post by JKyleOKC on 2012-05-31
Put the mouse pointer anywhere on the blank desktop and rotate the mouse wheel. If your icons re-appear, you've been bitten by the default behavior of Thunar's workspace switcher -- to switch workspaces with the mouse wheel on the desktop background!

On my slightly older Lucid system, there's an option in the Window Manager settings dialog to disable this. I don't know whether it's still there in the latest versions though. If not, it should be!

---

### Post by lei00 on 2012-05-31
Maybe it's juste a probleme with xfdesktop.
Did you try to relaunch it?

---

### Post by emreergecen on 2012-05-31
Thanks all :D Relaunching xfdesktop solved my problem :)

---

