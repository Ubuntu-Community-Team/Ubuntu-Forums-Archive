---
title: "Change boot order in grub"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by macakcira on 2013-11-08
OK, I want to change boot order in grub. I have Windows and Ubuntu, Ubuntu being on 1st place, now I want Windows to be on 1st place. How do I do that?

---

### Post by fantab on 2013-11-08
Do you just want to change the grub-menu order or do you want to make Windows boot by default?

This might help: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries)

---

### Post by SuperFreak on 2013-11-08
Grub Customizer might help.I believe it is in Software Centre

---

### Post by macakcira on 2013-11-12
Yes, I want just to change boot order in grub. Please don't make me use that customizer, because I used it before and after I moved Windows to 1st place I couldn't start Windows any more (it showed message [FONT=Ubuntu Mono]A Disk Read Error Occured. Press CTRL+ALT+DEL to restart[/FONT]) and I had to reinstall everything. I will try with that link you posted and I'll tell you if it worked.

---

### Post by fantab on 2013-11-12
> **SuperFreak said:**
> Grub Customizer might help.I believe it is in Software Centre

> **macakcira said:**
> Yes, I want just to change boot order in grub. Please don't make me use that customizer, because I used it before and after I moved Windows to 1st place I couldn't start Windows any more (it showed message [FONT=Ubuntu Mono]A Disk Read Error Occured. Press CTRL+ALT+DEL to restart[/FONT]) and I had to reinstall everything. I will try with that link you posted and I'll tell you if it worked.

Grub-Customizer is known to create issues, I was left with a bad taste in my mouth after recommending and using it on my friend's computer. 
Manually editing 'grub' files is simple and very neat. 
Just REMEMBER to **make backup copy of any system file you edit**. If things go south you can always fall back on the saved backup.

Good Luck...

---

### Post by macakcira on 2013-11-12
OK I got stuck on the beginning... 
In instructions it reads: "**Setting up a Grub background picture**

 You need to move 1 picture that is the same size as your screen resolution to **/boot/grub/** e.g. **sudo cp rain.jpg /boot/grub/**."

So I put the picture on my destop and run that command and it says: 
"cp: cannot stat &#8216;maslacak.jpg&#8217;: No such file or directory"

What am I doing wrong?

EDIT: OK I did it. I had to write full path to the file (oh I'm such a noob)...

---

### Post by deadflowr on 2013-11-12
> **macakcira said:**
> OK I got stuck on the beginning... 
In instructions it reads: "**Setting up a Grub background picture**

 You need to move 1 picture that is the same size as your screen resolution to **/boot/grub/** e.g. **sudo cp rain.jpg /boot/grub/**."

So I put the picture on my destop and run that command and it says: 
"cp: cannot stat &#8216;maslacak.jpg&#8217;: No such file or directory"

What am I doing wrong?

EDIT: OK I did it. I had to write full path to the file (oh I'm such a noob)...

Revised. as problem solved.

Edit and Added: Now that you've copied the image, did you run update-grub?

---

### Post by macakcira on 2013-11-12
Yes, yes, I did it, it works great! And now it's pretty too!

Thanks man!!!

---

### Post by thesleash on 2013-11-15
you could edit /etc/default/grub

probably it is a wise idea to make sure to have a live cd available and to back up that file, prior to changing it

to back up you could

sudo cp /etc/default/grub /etc/default/grub.back

---

