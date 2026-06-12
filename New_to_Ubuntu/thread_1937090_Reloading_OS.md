---
title: "Reloading OS"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by manners2345 on 2012-03-07
Hi:
   I am hoping to get some help!! At age 72, got bad eyesight, with glasses can see some with with big fonts, got bad hearing, no money for hearing aid, got really bad memory, seems to be getting worse, no help for that!!

   I would like to reload 10.04(LTS) OS starting from scratch. got no CD, do not know why, do not remember how to go about troubleshooting it!! Just will not read or do anything.

   So how do I clean up my hard drive??
    Dump current 10.04(LTS) and download and install new 10.04 across the Internet!! 
   Step by step instructions would be good so my wife can print them on a 3x5 card for me. My printing is mostly scribbling as my hand shakes so much.

Many thanks in advance!!!

---

### Post by Script Warlock on 2012-03-07
[here's]("http://www.psychocats.net/ubuntu/installinglucid") a simple to understand guide installing ubuntu 10.04.4 with screenshots.

download ubuntu 10.04.4 from [here]("http://www.ubuntu.com/download/ubuntu/download")

bad eyesight? hold down the ctrl key of your keyboard and scroll the scroll wheel up/down to any part of your browser. to return the default size of the browser just press ctrl+0.

---

### Post by mastablasta on 2012-03-07
here are the instructions for 10.04 LTS: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
 
or you can try with the community made manual: [http://ubuntu-manual.org/download/10.04e2/en_US/screen](http://ubuntu-manual.org/download/10.04e2/en_US/screen)
 
another easy one with pics: [http://www.psychocats.net/ubuntu/installinglucid](http://www.psychocats.net/ubuntu/installinglucid)

---

### Post by manners2345 on 2012-03-09
THANK YOU VERY MUCH!!! I will try!!!

---

### Post by manners2345 on 2012-03-10
I have tried the above suggestions.

As I said in my initial request, No CD R/W drive, it is there, physically,  but nothing happens!!

Tried creating start-up disk using USB, after several attempts was able to create one. Tried to use it on my laptop, seemed to start off okay, formatted drive, to 1 partition,ext 4. 

After a bit, installing, copying files like it should,completed thru step 7 got an I/O error and it stopped. Tried several times to redo always got an I/O error. So now I have a laptop with no system of any kind.

I have tried to redo USB flash drive, it gets to 96% complete then I get a check sum error. I have erased the flash drive, and have tried formatting to ext 4, then just erasing an making start up still get check sum error.

Is there any way of just putting terminal on a flash drive an apt-get in stall along with internet, then doing an install across the internet!!

---

### Post by mastablasta on 2012-03-10
It is called mini iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Here is a how to with pictures: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

it owuld still be a good idea to check the downloaded iso and make sure using md5sum that it is exactly the same as the one on the server. here is how you check that after download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

it could be that your download had some small errors in it which are no good if the file is used to isntall operating system. checking the md5sum after download makes sure it is a good download. it could be that faulty download caused your error. 

alternatively if you used torrent to download the file, then this is done for your during download.

---

### Post by grahammechanical on 2012-03-10
Could you consider this?

[http://shop.canonical.com/product_info.php?products_id=952](http://shop.canonical.com/product_info.php?products_id=952)

I know it is not 10.04 but it would save all the fuss about creating a USB stick.

And 11.10 has these massive (in size)  icons in a Launcher panel down the left side of the screen that launch programs.  We are moving away from menu lists. 

This will give you an idea of what you get with 11.10

[http://www.ubuntu.com/ubuntu/features](http://www.ubuntu.com/ubuntu/features)

And there are improvements to accessibility features in the soon to be released 12.04.  Here is a publicity quotation:

> Accessibility is central to the Ubuntu philosophy. We believe that  computing is for everyone regardless of nationality, race, gender or  disability.

You are the kind of user that is needed to test out some of these accessibility features.

Regards.

---

### Post by manners2345 on 2012-03-12
A Really BIG BIG LOL!!
I doubt it at my age, I am no where even close to being PC

Got CRS (Cannot Remember Stuff)

First got into computers in 1964 Learned how to program IBM1401 with Autocoder, really liked it!!!Just a rhetorical question, How old were you 1964??
Then I joined the Navy, went to BEEP School(Basic Electronics and Electric Preparatory) in San Diego
Then the Navies ET A1,2 School at Treasure Island near San Francisco
Then off to DS(Data Systems) A School at Mare Island Calif., after A School went to DISPLAY C School at Mare Island.
Then went aboard ship an off to Vietnam.
In January 1970 went back to Mare Island for Senior Systems Technician C School. 
Then to Damneck Virginia with a short stop at at the Naval War College in Newport R.I, of about 6 months.
At Damneck was assigned to an R&D Project called SHORTSTOP, spent  almost 4 years at that.

Back then if you were into computers, you had to be able to walk, chew bubble gum and whistle a HAPPY TUNE all at the same time.

After I got out of the Navy, I was literally a Basket Case for 6 months!!

Taught computer systems at a non-profit for a bit, then pulled the plug in OCT. 2001

---

### Post by manners2345 on 2012-03-12
using CD's are like using 5.25 floppies, flash drive are better an more reliable

---

### Post by manners2345 on 2012-03-12
this is one of the checksums I get old-dude@old-dude-desktop:~$ md5sum  ubuntu-10.04.4-desktop-i386.iso
a7fc1189579c41605391e2bfaea94aa2  ubuntu-10.04.4-desktop-i386.iso
old-dude@old-dude-desktop:~$ 

not even close this the 3rd I have gotten not even close!!! 

This from the last bit torrent down load

---

### Post by manners2345 on 2012-03-12
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
 

Can I specify which desktop I want?? such as  10.04.4

---

### Post by bkratz on 2012-03-12
> **manners2345 said:**
> this is one of the checksums I get old-dude@old-dude-desktop:~$ md5sum  ubuntu-10.04.4-desktop-i386.iso
a7fc1189579c41605391e2bfaea94aa2  ubuntu-10.04.4-desktop-i386.iso
old-dude@old-dude-desktop:~$ 

not even close this the 3rd I have gotten not even close!!!


If you use the bit torrent download (as stated in post 6) , it will be correct when you finish downloading.  It is checked during reception and retransmitted if wrong.

---

### Post by audiomick on 2012-03-12
> **manners2345 said:**
> this is one of the checksums I get old-dude@old-dude-desktop:~$ md5sum  ubuntu-10.04.4-desktop-i386.iso
a7fc1189579c41605391e2bfaea94aa2  ubuntu-10.04.4-desktop-i386.iso
old-dude@old-dude-desktop:~$ 

not even close this the 3rd I have gotten not even close!!! 

This from the last bit torrent down load

I have also observed this. I came to the conclusion that the posted md5sum was still the one for the first 10.04 image, and it was already up to 10.04.3 when I tried it, i.e. they hadn't updated the md5sum.

The image I had downloaded worked fine.

---

### Post by Megaptera on 2012-03-12
Hi manners 2345,
Have you considered using Vinux? (Quote) "Vinux is a remastered version of the popular Ubuntu 10.10 Maverick Meerkat distribution optimised for the needs of blind and partially sighted users."
More here: [http://vinuxproject.org/about](http://vinuxproject.org/about)

Hope this is of interest?

---

### Post by Jerry N on 2012-03-12
> **manners2345 said:**
> ...Just a rhetorical question, How old were you 1964??...

Older than you were:P:P:P

In those days, I was designing analog electronics for military flight system simulators and trainers.

Jerry

---

### Post by manners2345 on 2012-03-12
tat was a bit torrent

---

### Post by manners2345 on 2012-03-12
so you may have been working with Navy TD's

---

### Post by manners2345 on 2012-03-26
I have finally been able to create a supposed boot disk using start
up disk creator on a USB Flash Drive, it went from start to finish with no errors. It was a torrent download. Tried to boot to both my desk top and old laptop, nothing happens. If I double click wubi.exe this what I get

Archive:  /media/9789-844C/wubi.exe
[/media/9789-844C/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/9789-844C/wubi.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/9789-844C/wubi.exe or
          /media/9789-844C/wubi.exe.zip, and cannot find /media/9789-844C/wubi.exe.ZIP, period.

If I go to autorun.inf, this is what is there



[autorun]
open=wubi.exe --cdmenu
icon=wubi.exe,0
label=Install Ubuntu

[Content]
MusicFiles=false
PictureFiles=false
VideoFiles=false

So where do I go from here???

---

### Post by manners2345 on 2012-03-27
I posted this to my thread about reloading OS, about 48 hours ago, got no response:confused:.
Does that mean no one has an answer!!

I have finally been able to create a supposed boot disk using start
up disk creator on a USB Flash Drive, it went from start to finish with no errors. It was a torrent download. Tried to boot to both my desk top and old laptop, nothing happens. If I double click wubi.exe this what I get.

Archive: /media/9789-844C/wubi.exe
[/media/9789-844C/wubi.exe]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
note: /media/9789-844C/wubi.exe may be a plain executable, not an archive
zipinfo: cannot find zipfile directory in one of /media/9789-844C/wubi.exe or
/media/9789-844C/wubi.exe.zip, and cannot find /media/9789-844C/wubi.exe.ZIP, period.

If I go to autorun.inf, this is what is there



[autorun]
open=wubi.exe --cdmenu
icon=wubi.exe,0
label=Install Ubuntu

[Content]
MusicFiles=false
PictureFiles=false
VideoFiles=false

So where do I go from here???

---

### Post by sffvba[e0rt on 2012-03-27
Threads merged.


404

---

