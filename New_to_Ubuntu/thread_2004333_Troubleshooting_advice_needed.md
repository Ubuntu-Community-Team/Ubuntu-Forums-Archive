---
title: "Troubleshooting advice needed"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by PcMojo on 2012-06-15
I was hoping somebody could offer me some troubleshooting advise. I have a Dell D620 that worked perfectly on 10.10. After upgrading to 12.04 the Cd/Dvd won't burn anymore. It will read and acknowledge that a blank Cd has been inserted, but won't burn – it will give me an error telling me to insert the correct medium. I thought it may be an issue with Brasaro so I installed K3b, but have the same problem. If this was M$ I would suspect a driver. I assume Linux has drivers too but am not sure where to look. If it worked on 10.10 can't I just identify and replace the new driver with the old one? Does anyone have any ideas on how to troubleshoot this issue? Thanks in advance!

---

### Post by PcMojo on 2012-06-15
Update- It's been several weeks since I noticed this issue, so I decided to retest the Cd/Dvd burner to see if the symptoms have changed. When I insert a blank Dvd, it makes a strange succession of noises and nothing happens (deet-deet, deet-deet-deet repeated with the light blinking), when I start Brasero manually it will ask for the correct medium type. When I put in a blank Cd the auto play menu appears asking, telling me it notices that it is a blank writable Cd, and asks what I want to do with it. Neither Brasero or K3b are given as options. When I manually start Brasero or K3b, it shows them starting in the taskbar, then the program just closes and disappears. Any ideas on how to troubleshoot this?

---

### Post by Curtis6767 on 2012-06-15
Does your DVD player work, otherwise? Just a long shot below.

 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by PcMojo on 2012-06-16
Thanks for the response. Glad you asked that question. I assumed other functions worked because previously burned Cds/Dvds seem to work fine but after you asked the question I inserted a music Cd from the manufacturer and it didn't work, it produced an error on Movieplayer that said, “Could not open location; you might not have permission to open the file”. When I tried the same Cd's on RhythmBox, it sort of worked. It would play - but if I paused a track and tried to restart by pushing pause/play, RhythmBox would just lock up. To be honest, I don't know if I ever tried playing a manufacturer's Cd on 10.10. I could read and right to burnable Cd's and Dvd's, but I don't know if I ever tried to play a music Cd (ripped them all to mp3's years ago). I can boot up previously burned Linux live iso Cd's but I can't burn them. But what is so strange is that it all seemed to work perfectly on 10.10. Do you know if there is a way for me to find what file controls this so I could replace it with the old 10.10 version?

---

### Post by Curtis6767 on 2012-06-16
I'm sure by now you've gone into System Settings and searched for additional drivers so if you were to enter the following code into a terminal, it will list all your hardware. With the info you may be able to check to see if there is a new driver for your burner. The information may also be helpful to someone else who has a better understanding of these types of things because I don't.

```
sudo lshw
```

GL

---

### Post by Cheesehead on 2012-06-16
Check your permissions:

See who can read/write to the CD drive:
```
$ ls -l /media
total 20
lrwxrwxrwx 1 root cdrom    6 2009-07-07 15:50 cdrom -> cdrom0
drwxrwxr-x 2 root cdrom 4096 2009-07-07 15:50 cdrom0
```
In this example, only root and members of the "cdrom" group have access to write to the CD drive. Anyone can read from it.

Who is in that group?
```
$ cat /etc/group | grep cdrom
cdrom:x:24:big-frank,root
```
The users big-frank and root are in that group, and so have write access to the CD Drive.

---

### Post by PcMojo on 2012-06-17
@ Curtis6767
 Lshw gives me this for cdrom:
  *-cdrom 
                 description: DVD reader 
                 product: CDRW/DVD TSL462C 
                 vendor: TSSTcorp 
                 physical id: 1 
                 bus info: scsi@1:0.0.0 
                 logical name: /dev/cdrom 
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd 
                 logical name: /dev/sr0 
                 version: DE01 
                 capabilities: removable audio cd-r cd-rw dvd 
                 configuration: ansiversion=5 status=nodisc 



 the description bothers me as it just says “reader” but it does show CDRW under product which shows writing capabilities. Of course, I am assuming the information is just text labels inputed by some programmer and not necessarily accurate. Hopefully I'll be able to use the make & model to find a driver if that ends up being the fix. Thanks for your help!

---

### Post by PcMojo on 2012-06-17
@ CheeseHead – Thanks for the response.
 My output doesn't look anything like yours:
 $ ls -l /media 
 total 0 
 

 Do you think that is what the problem is? What does total 0 mean? Is that saying that nobody has writing permissions? My output for your second command is the same as yours except it doesn't list root. I'm sort of confused now. If my login name is listed in the second command, then why is the first command coming back with total 0?

---

### Post by PcMojo on 2012-06-20
After doing some research on permissions, I am unable to find much for *buntu on this issue. I found some information for other flavors of Linux. One article said to add the line “chmod 666 /path/to/device” to etc/rc.local, but my rc.local is all commented out and says “by default this script does nothing”. I am assuming that it is a legacy file and that there is a newer way to go about this. Anyone have any ideas?

---

### Post by PcMojo on 2012-06-23
Part of the problem was that in researching the drive, I found it only reads DVDs, it doesn't write DVDs. :oops:  But, for some reason it was still acting the same way with CD's when I know it can write. Other forum posts were saying to add a burning group for writing permissions. The also recommended using K3b's setup to add the "burning" group, but it wouldn't let me, so I just added the burning permissions to the cdrom group in K3B. Now it sort of works. I can burn an .iso. For some reason I can't do it from Brasero or K3B natively, I have to insert a CD and wait for the "what application do you want to use", otherwise neither application will recognize the disc. For multiple burns I have to shut the application down and start the process over.  Thought I'd follow up in case anyone else could learn from this.

---

