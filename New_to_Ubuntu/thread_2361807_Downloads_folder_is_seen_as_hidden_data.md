---
title: "Downloads folder is seen as hidden data"
date: 2017-05-21
forum: New to Ubuntu
---

### Post by andrew2622 on 2017-05-21
Hello everybody,
    

     I used to have a perfectly running Ubuntu 14.04 until the disaster has struck due to my ignorance and now I"ve lost my "Downloads" folder - 40GB without any trace.

    I ran Testdisk on the hard drive (160Gb) and I've got the message:


  " Hidden sectors are present.

    size 312500000 sectors
    user_max 312500000 sectors
    native_max 312500000 sectors
    dc0 312500000 sectors

    Drive Configuration Overlay (DCO) present.

    Continue even if there are hidden data. "


    This very hidden data is the data I need to recover and Testdisk cannot access it.

    
    How I got here: I tried to tidy up my Ubuntu 14.04  and from "Home" folder I had deleted some "unnecessary" folders  like "Public", "Templates", "Examples" and I've renamed others.

    Then I tried to do the same with the "Downloads" folder, but when I wanted to open it, I got the message: " the folder contains unreadable data and the content cannot be displayed"; however I had opened it before I've played with the "Home" folders!!

    Next I've restarted the computer but the "Downloads" folder couldn't be found - it disappeared without any trace; however the free space on the hard drive has been increased by 40 GB the size of this folder.

Now my "Downloads" folder became the hidden data!!

What can I do? Please help me!


    Thank you very much,

    Andrew

---

### Post by ajgreeny on 2017-05-21
Run command ```
ls -lahp --group-directories-first Downloads
``` and report back here the output from that which might give us some clue what is going on, though I suspect this may be more to do with disk or filesystem faults than unreadable files.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by andrew2622 on 2017-05-23
Hello everybody,

Thanks ajgreeny for your reply.

I've ran the command and I've uploaded the screenshot of the terminal window: Screenshot3

I need to mention that I used to have two "Downloads" folders, one that can be accessed from the "Home" folders only and the 
second one that used to be listed under the "Home" and "Documents" and this is the one that disappeared - and then the system 
has generated automatically a bookmark for the missing "Downloads" folder: Screenshot2

By clicking on this bookmark the system generates a  popup window with an error message: Screenshot1


Thank you,

Andrew



  	 	 	 	   [COLOR=#000080][U][URL="http://s94.photobucket.com/user/mihai262/media/Screenshot_3_zpszbummvl7.png.html?o=0"]http://s94.photobucket.com/user/mihai262/media/Screenshot_3_zpszbummvl7.png.html?o=0

[/URL][/U][/COLOR]

  [COLOR=#000080][U][URL="http://s94.photobucket.com/user/mihai262/media/Screenshot_1_zpspvxbcrib.png.html?o=2"]http://s94.photobucket.com/user/mihai262/media/Screenshot_1_zpspvxbcrib.png.html?o=2

[/URL][/U][/COLOR]

  [COLOR=#000080][U][URL="http://s94.photobucket.com/user/mihai262/media/Screenshot_2_zpsd99jsiv1.png.html?o=5"]http://s94.photobucket.com/user/mihai262/media/Screenshot_2_zpsd99jsiv1.png.html?o=5



[/URL][/U][/COLOR]

---

### Post by ian-weisser on 2017-05-23
Since you showing us mere terminal output, are the screenshots really necessary?

It's usually faster and easier for everyone if you simply copy-and-paste the test, keeping the formatting by using [code] tags.

---

