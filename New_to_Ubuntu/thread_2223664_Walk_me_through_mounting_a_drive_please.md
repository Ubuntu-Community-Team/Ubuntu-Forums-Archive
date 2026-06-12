---
title: "Walk me through mounting a drive please"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by lile001 on 2014-05-12
Long story short, I am sitting here at a computer with only a terminal prompt, because I broke the video somehow.  I think I have  the solution here on a thumb drive, but I can't read the thumb drive when I stick it in the slot.  Clearly out of my league, but whatever that's why we play in linux-land.  Let's take one step at a time:  When I stick a thumb drive into the dead box, I can see it in /media but cannot access it.  I see a device called /media/FC30-3D89.  I cannot cd to it to run my driver file, it says Permission Denied even if I am Su.  What steps do I take to be able to read it?

---

### Post by steeldriver on 2014-05-12
Can you

```

cd /media

ls -l

```

or

```

ls -l /media

```

If so what permissions are listed for FC30-3D89

Also what does

```

mount | grep media

```

show?

---

### Post by oldfred on 2014-05-12
You normally install video drivers from the repository.

Can you boot second grub menu, or recovery? That uses nomodeset by default.

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

