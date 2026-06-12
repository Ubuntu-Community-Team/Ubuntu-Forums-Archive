---
title: "security problems"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2013-01-08
I am having another family member go on my Linux box. and asked her not to download anything but she dose anyway while i am at work. To make matters worse I only have an 80 gig hard drive in it. so am just asking how can I stop this dead in it's tracks.  Even from the quest Session. were only I  can go on it????:confused:

just to let her go online but no downloading to the hard drive

She is not using a quest account  she is using my account ??
  

i dont want her in the quest account just no downloading mostly because i only have an 80 gig hard drive

---

### Post by chadk5utc on 2013-01-08
> **RemmyNumber7 said:**
> I am having another family member go on my Linux box. and asked her not to download anything but she dose anyway while i am at work. To make matters worse I only have an 80 gig hard drive in it. so am just asking how can I stop this dead in it's tracks.  Even from the quest Session. were only I  can go on it????:confused:

I think most versions of Ubuntu have a guest account which you can enable if not already, or add a new user and restrict that accounts access.

---

### Post by Dreamer Fithp Apprentice on 2013-01-08
Sounds like he's already got her on the guest account.

Use gparted to create a small partition for her and adjust her account so her home is in that partition and she can't access anything else. When her partition fills up tell her she has to get her own drive or buy you a bigger one.

---

### Post by arpanaut on 2013-01-08
Disable the guest account.
Log into your account with a password that only you know.
Done Deal

---

### Post by Dreamer Fithp Apprentice on 2013-01-08
Presumably he doesn't want to lock her out completely or he wouldn't have posted. 

Some other approaches. You can change file permissions so she can read but not write to the drive. If you use a common data directory or better yet, a data partition separate from the system directories, you can mark the top data directory or the root directory of the data partition recursively so only owner and some group can write to it or change it but anyone can read it. Make yourself part of the group but not her. That way she can read your stuff but not change or delete it or put anything else on your drive.

 If you really want to get really fancy and totally secure, use remastersys to make her a live disk and don't give her the admin password, just a user pass. Don't put her in the sudoers list. Set it up so she can't even mount your hd. Then she had full use of your machine but CAN'T touch your data in any way. She can't even screw up her OWN account because no changes she makes survive a reboot. And you won't be out ANY hd space since once you put her system on CD you can delete it from the HD and use the space for your own purposes. It's idiot proof, girl friend proof, even mother-in-law proof. If she were an expert and WANTED to damage your system, she'd have to use a hammer. And you won't be called on much for tech support because she CAN'T break it in any way a reboot won't fix.

---

### Post by Cheesehead on 2013-01-08
Add a logout script to her account to delete everything in her (download) Desktop directory. Or the Guest Account's desktop.

If she wants to save it, she needs to save it elsewhere (like a USB stick) before logout.

---

### Post by ubudog on 2013-01-08
> **cheesehead said:**
> add a logout script to her account to delete everything in her (download) desktop directory. Or the guest account's desktop.

If she wants to save it, she needs to save it elsewhere (like a usb stick) before logout.

+1

This is a good solution and does not force her to quit using the computer completely.

---

### Post by Impavidus on 2013-01-09
I think you can set disk quota. You'll have to install the **quota** package. I've no experience using it on linux, but it worked on solaris (unix), where I wasn't the administrator. That way you should be able to give her a normal account (login, no sudo) and limit her disk usage to, let's say, 10GB, without creating a special partition for her. This makes it easier to change the limit at some point.

Is there anyone here who has experience using disk quota on ubuntu?

---

### Post by Paqman on 2013-01-09
> **RemmyNumber7 said:**
> Even from the quest Session.

The Guest session's home folder is located in /tmp. /tmp gets wiped at every boot. So simply restrict her to the Guest Account and if she fills her home folder up with data, just reboot.

---

### Post by RemmyNumber7 on 2013-01-11
how do u do this ???

---

### Post by zombifier25 on 2013-01-11
> **RemmyNumber7 said:**
> how do u do this ???

If she has her own account, remove/lock it, and she'll be forced to use the guest account.
If she's using your account, change the password, and she'll be forced to use the guest account.

All of this can be done by clicking your name in the top right > User Accounts.

---

### Post by RemmyNumber7 on 2013-01-22
she dose not use the guess account she uses my account. How do you set up file permissions on Ubuntu 12.10. Is it possible to put a password on a file's in the home directory ????.   Or how do would you block url's from loading in fire fox browser. she lives on face book and downloads movies like crazy.  Just trying to stop the take over of my laptop that all.

---

### Post by RemmyNumber7 on 2013-01-22
she dose not have her own account i checked. i changed my password twice and the next day when i come home from work there she is she is on it. how is this happening ?????.

---

### Post by Dreamer Fithp Apprentice on 2013-04-19
> **RemmyNumber7 said:**
> she dose not have her own account i checked. i changed my password twice and the next day when i come home from work there she is she is on it. how is this happening ?????.Good question. Some possibilities that occur to me off the top of my head:

1-You are useing very obvious passwords and she is guessing them. This is probably the single most common and most exploited security mistake. It doesn't take that long to try a few hundred likely possibilities. Use a pass phrase that is longer and contains some mispellings or non-words and some odd characters. Something like:
```
vEd! o% liveanamjero fi erin go braless but with chartreuse pants~

``` would do nicely. Make up your own of course. Don't use that one. After all, she may hang out here. Which thought brings me to possibility 2:

2-She may be really, really, really, really, really smart and has figured out how to hack past a good password, perhaps starting by booting with some sort of special purpose thumb drive based system to find out your pass and then she is just rebooting in your system because it appeals to her sense of humor. Encrypting your home partition would probably make that a bit harder to do, but realisticallly, if that is what is happening, give up, you're outclassed. Your best strategy is to introduce her to me and hope she'll marry me so you can get her out of the house.

3-She get's the password from watching you log in. After all, it isn't THAT hard, especially if you type slowly and it isn't a long password. Maybe in the future you could only log in in the dark. 

4-She installed a hardware keylogger.

5-She's a mind reader.

6-You talk in your sleep. Or say things you don't remember when you are REALLY altered. Or she gave you a mickey finn with truth serum and something else to make you forget you told her your pass phrases.

7-She's not a mind reader, but she KNOWS one.

8-You're writing your pass phrases down somewhere (or wheres) you think she'd never look but you're wrong.  Taped to the underside of the keyboard is less than optimal. In your wallet is not necessarily safe. Tatooed to the inside of your eyelids works pretty well if you can focus that closely.

_**9-Before you changed the pass phrase, she enabled the root account so she can surf as root, or use the root account to look up your pass phrase and then reboot. This is actually a pretty strong possibility and the one I'd bet on.**_ I'm not sure how to tell you to check out that possibility and what to do about it without telling you how it is done, which is utterly taboo here and I think there are admins who would love an excuse to ban me. But possibly that is enough of a hint for you to use Bing (or Google, but Google is Evil) and study up on the subject. If that is what she did, just do it back unto her the same way she did it in the first place. And then change your regular user password immediately after. If that is what happened she should now be without EITHER password and the mystery and problem are solved. This borders on an example of case 2 above, but it isn't sufficient inducement for me to help you to get her out of the house in the fashion suggested.

_**There are some some solutions that will deal with any of 1 - 8 above (but not 9) or any OTHER way she might get your pass phrase:**_

You might could find a log in manager that requires a "token" like a file on a usb thumb drive in order to log in. I've never looked for one but, given how serious some people's security requirements are I'd be surprised if they don't exist.

I believe you can use either PGP (and possibly GPG), Truecrypt, or Scramdisk to encrypt your entire drive, including the operating system, everything but the first half kilobyte where your MBR and similar beasties live. I'm pretty sure you can set up a Truecrypt encrypted drive to absolutely require a "token" thumb drive with key files on it in order to boot. Probably you can do the same with the others. So in either of those cases, you just keep the thumb drive on your key chain and back up copies somewhere at work where she couldn't possibly get to them.

PCs always used to come with actual keys that let you lock them off. If yours doesn't have one, I'll bet you could buy a lock and install it although I haven't looked for one. This probaly isn't as secure or as cheap as the disk encryption method. 

There are biometric hardware devices like finger print readers you can buy that are supposed to be able to prevent unauthorized people from logging in. They are probably expensive but I haven't looked.

You can simply put the whole PC or just a crucial part of it, like the power cord or the mouse, or even the hard drive, in a locking drawer, cabinet or room. Or carry it with you. Be careful with the hard drive though. If you start unplugging and plugging in your hard drive be extra special sure you back up your data. Of course, you do that anyway, right?

Or you could rig up your keyboard so that anybody who doesn't know how to disarm it is squirted with skunk juice and fish emulsion.

Good luck. I'd be curious to know what you find out and what you do.

---

