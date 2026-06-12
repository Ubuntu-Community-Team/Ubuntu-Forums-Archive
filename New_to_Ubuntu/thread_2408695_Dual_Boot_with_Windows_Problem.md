---
title: "Dual Boot with Windows Problem"
date: 2018-12-21
forum: New to Ubuntu
---

### Post by graydonhope on 2018-12-21
Hey guys, 

This is my first post here, so I apologize if I am not in the correct place and/or am repeating a question. I have searched online and haven't found the solution I am looking for yet.

I attempted to dual boot Ubuntu onto my old Acer Aspire E1. I successfully got Ubuntu on, but lost my Windows. However, I can still see and access all my Windows files (through the file browser on Ubuntu). When I try to run Windows from startup I get an error saying "No partition device"  then it switches to "no bootable device found". I understand there are many posts about this, but I haven't had any luck. I installed lilo and tried to "fix/recover" the mbr, but still no luck. 

What is different in my situation from what I see on most posts to fix this is that my laptop is quite old and does not have a lot of these options in the BIOS menu. For example I do not have the option to select "UEFI file as trusted for executing" in the security tab. 

I don't know if it helps, but I have tried using the BIOS menu before to allow virtualization for Android Studio's emulators, but my laptop doesn't support it. I believe this is what is giving me difficulty and makes my case different.

If you cannot tell, I am very new to this.. Any help is appreciated as I am pretty stuck.

I would also like to keep all my files on windows without losing them!

Side note: How do you "properly" pick the booting order in the BIOS menu? Mine has been through trial and error.

Thanks

---

### Post by yancek on 2018-12-21
There are countless possibilities that prevent booting and/or dual booting so the best thing to do is to post as much information as possible.  How old is the Acer?  CPU? RAM? 

To get information, I would suggest that you go to the link below to boot repair.  Use the 2nd option explained on that page to download boot repair and then use their instruction to run the option to Create BootInfo Summary and do NOT try to make any repairs.  When boot repair finishes, it should give you a link which you can post here and it will show necessary details on your system and hopefully, someone will have a solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jdeca57 on 2018-12-21
First is the fact that you have access to your data. Make a backup on an usb stick or hard drive. Second is the fact that you can always restore (a recent) windows by rewriting the boot member and killing grub so that you revert to a windows system and then make a backup. So, with your data safe you can go for a dual boot system between a version of windows and a version of ubuntu. Mostly the order of booting in bios is only a concern when installing a new OS and you seem to have solved that problem so the question that remains is one we can't answer: do you really need the old windows version on that PC?

---

