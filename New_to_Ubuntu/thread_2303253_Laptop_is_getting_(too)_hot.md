---
title: "Laptop is getting (too) hot"
date: 2015-11-17
forum: New to Ubuntu
---

### Post by diho on 2015-11-17
Hello everyone,

I have used ubuntu before, sadly due to driver problems I was forced to stop using it.

Now I want to try it again, hoping that new drivers are available. Sadly I am still having problems.

My laptop is getting hot (around 60 degrees celcius). I have no clue what this is causing this.

I have a HP elitebook 8570w with a Firepro M4000 graphics card.

Hopefully someone can help me with identifying and fixing the problem.

Kind regards,

Diho

---

### Post by mastablasta on 2015-11-17
install 15.10
install AMD proprietary drivers.

---

### Post by diho on 2015-11-17
Thanks for your reply, I have installed 15.10. But the proprietary drivers makes it unable to boot (black screen after bios)

---

### Post by mastablasta on 2015-11-17
do you maybe have dual graphics? if so, then you need to initialize the drivers first after you install them. : [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

so remove drivers, reinstall, initialize and then reboot (follow the guide in link)

not all hybrid laptops/desktop are compatible with Linux. depends if manufacturers decided to support it under Linux or not.

---

### Post by diho on 2015-11-17
I don't have dual graphics, just the firepro m4000 card.

---

### Post by leunam12 on 2015-11-17
How old is your computer? Maybe it has dust inside blocking the air vents.

---

### Post by diho on 2015-11-17
Maybe 2 years old. But since windows isn't cause this problem i guess dust isn't causing this heat

---

### Post by brian-mccumber on 2015-11-17
You would be surprised at how much dust laptops can accumulate over a short period of time even if you think your house is clean. I take my laptop apart once every two to three months and blow the dust out of it with an air compressor and a wand. Anything that is electronic has an electromagnetic field around it that actually collects dust like a magnet. You can see the external cooling slots in the laptop but you can't see where the fan is and that is where the dust likes to pile up.

---

### Post by diho on 2015-11-17
That is true, but I have a dualboot. Windows is fine, just Ubuntu is giving me this problem, so I really dont believe that dust is causing this.

---

### Post by mastablasta on 2015-11-18
read this: [http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-fglrx-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-fglrx-Fix)

at the bottom is a link to solution (workaround) until AMD patches this mess.
there is a bug in driver. another option would be to maybe use 15.04 and then try the proprietary.

maybe a version of 14.04 would work as well. you could try it and install AMD drivers.

internet says it's a GCC issue as apparently drivers work well in same kernel under 15.04. The interesting things is that usually AMD works with Ubuntu to release drivers on time.  and looks like they worked together now as well but that Ubuntu added something later on. usually these kind of issues are resolved in a month or so from release. for home user it is best to use 14.04 if it works. for new hardware latest version usually has the most compatibility. you say computer is 2 years old. so that's form 2013 then. 14.04 might work well especially with a bit newer kernel.

---

### Post by QIII on 2015-11-18
Ubuntu 15.10 is provisioned with GCC 5.  Unfortunately, the fglrx driver compiles with GCC 4.9, so it barfs on 5.0.  The committed fix provisions Wily with GCC 4.9 to compile fglrx.  The wily-propsed package works, but some users might not understand how to set things up to selectively install from -proposed.

Just FYI.

---

### Post by diho on 2015-11-18
[FONT=arial]@[/FONT][SIZE=1][FONT=arial]mastablasta, @Qlll
[/FONT][/SIZE][SIZE=1][FONT=arial][COLOR=#000000]
[/COLOR][/FONT][/SIZE][FONT=arial]Thanks for your answers! I will wait for a permanent fix for this problem, hopefully they will be quick with it.[/FONT][SIZE=1][FONT=arial][COLOR=#000000]


[/COLOR][/FONT][/SIZE]

---

### Post by diho on 2015-11-21
A little update, it seems that my videocard isn't causing this heat. This is the situaton:
- I am just browsing the web or using a simple text editor.
- The laptop is placed on a table, so no pillow or whatever.
This is the result:

[IMG]http://imageshack.com/a/img908/4024/3Zi1zO.png[/IMG][IMG]http://imageshack.com/a/img905/2685/V5KWfE.png[/IMG]

In my opinion are the cpu core temps way to high for the current load.

With this new info, does anyone know how to fix this?

Edit: over time the cpu core temps go up to 56  (all), no significant changes in the load.

---

### Post by diho on 2015-11-22
Anyone? Please, this issue is really annoying. It makes it quite impossible to work with like a virtual machine because with that load the temp is rising fast like a rocket.

---

### Post by mastablasta on 2015-11-23
It doesn't seem high to me. I have and older version Celeron which is I think P4 upgraded. those were hot. anyway. I get between 50 and 70 C.

check the operating temp for your CPU online and you will see if it is hot or not but 45 or 50 C is not hot. hot is over 90 C.

CPU heats up in order to work fast. but here I am not sure what temp6 is - that one is a bit too hot.

edit: just checked online a bit and seem your temps are normal. but apparently you can use this to determine any abnormalities: [URL="http://www.intel.com/support/processors/sb/CS-031726.htm"]http://www.intel.com/support/processors/sb/CS-031726.htm
[/URL]
for example i5-3317U has Tjunction (max temp allowed to run on the dye) at 105 C. so fans will work hard when it reaches 90 or something like that to keep it there.

---

### Post by diho on 2015-11-23
@Mastablasta,

Hm okay but my fans are making quite some noise when the temp gets to 60. While when I am running Windows, they won' t be making this much noise. 

But as long as it isn't too high I guess it's fine. Thanks for your help!

---

### Post by mastablasta on 2015-11-24
fan speed is another matter. I think you could regulate that or maybe there is a setting that has to be enabled for the fans to work properly. not sure what that is.

by the way... I read some stories about some HP users upgrading from 7 to 10 only to find out that HP cool sense tech (or whatever that is called) is not running so they would then have this fans working a bit loud in 10 but not in 7. official advice from HP to solve the issue safely was to downgrade to 7.

---

