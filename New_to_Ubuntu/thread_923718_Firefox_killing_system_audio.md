---
title: "Firefox killing system audio?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-18
I've been having an issue that seems like whenever Firefox needs to use sound and video that the rest of the system has its own capabilities for sound and video stripped until Firefox is done using it. I'm not sure how to fix this or even if it's fixable, and was hoping someone knew of a way to make it so that Firefox doesn't hog sound channels like that, as it can get old very fast. :confused:

---

### Post by Bakon Jarser on 2008-09-18
*sigh* Another pulseaudio problem.  Why hasn't ubuntu issued an update when a fix has been available for so long?

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Grimhound on 2008-09-18
> **Bakon Jarser said:**
> *sigh* Another pulseaudio problem.  Why hasn't ubuntu issued an update when a fix has been available for so long?

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

When I try to do step 1:
> $ mkdir ~/pulse-backup; sudo mv ~/.asoundrc* /etc/asound.conf ~/pulse-backup/
it gives me this error,
> bash: $: command not found
mv: target `/home/matthew/pulse-backup/' is not a directory


Any idea?

---

### Post by Bakon Jarser on 2008-09-18
I suggest reading the line directly above that command.

```
1. Backup important configuration files (don't worry if you see "no such file or directory" warnings):
```

Don't ever just copy and paste blindly.  Read about what you are doing.  It may be important.

---

### Post by mc4100 on 2008-09-18
> **Grimhound said:**
> When I try to do step 1:

it gives me this error,


Any idea?
The first command should have created that directory:
```
mkdir /home/matthew/pulse-backup && sudo mv ~/.asoundrc* /etc/asound.conf ~/pulse-backup/ 
```
edit: Ah, it's because you straight copied and pasted (thus including that "$").

---

### Post by Tatty on 2008-09-18
If this appears to be with flash applications, then there is a fix in the repos.

```
sudo apt-get install libflashsupport
```

Info on it here: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by Grimhound on 2008-09-18
I tried everything and it's as fussy as ever, sadly. Do any of you know if 8.10 is going to be continuing with this BS, or are they sorting this out?

---

### Post by mc4100 on 2008-09-18
> **Grimhound said:**
> I tried everything and it's as fussy as ever, sadly. Do any of you know if 8.10 is going to be continuing with this BS, or are they sorting this out?

They're shipping a new pulseaudio (i think), Firefox 3.0.2, and Flash 10 .. so it should be fixed.

Edit: Fixed "there" to "they're" ... I'm an idiot.

---

### Post by Grimhound on 2008-09-18
> **mc4100 said:**
> There shipping a new pulseaudio (i think), Firefox 3.0.2, and Flash 10 .. so it should be fixed.

Ah. Good.

Well, after all that and swapping out Totem for Gecko, it seems to be working nicely.

---

### Post by sunwukim on 2008-09-30
After Firefox 3.0.3., I too lost sound on Youtube, and others. 

I used the following:  

sudo apt-get install libflashsupport

and nothing else, and this worked for me in Hardy 8.04. Thanks for this thread!
Without these spaces, noobs like me would drown....

---

