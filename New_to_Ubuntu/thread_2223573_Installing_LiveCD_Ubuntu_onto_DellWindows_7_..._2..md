---
title: "Installing LiveCD Ubuntu onto Dell/Windows 7 ... 2.0"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by john215 on 2014-05-11
As the title alludes to, this post is a response to a prior post ([http://ubuntuforums.org/showthread.php?t=2223172](http://ubuntuforums.org/showthread.php?t=2223172)) and as such I felt I need to preface the post which the comments below. My question/concern is in **bold black** down below.

Coffeecat, I  respectfully ask you to reconsider your decision.

Correct me if I am wrong, would not a penetration tester used a lot of the same tools/techniques that a “cracker” would? Your attempt to frame these tools/techniques as inherently sinister is specious at best. It is the intent of the person running the tools/techniques that frames these techniques.

Nevertheless, I did sympathize with your desire not to have this topics discussed, openly and potentially, in detail, in your forum, however, the direction and the substance of the thread was entirely legitimate (getting the LiveCD of Ubuntu to boot) until humbly, you injected ‘cracking’ into the conversation and then preemptively closed the discussion, presumably, on the assumption that it would led down a sinister path, when ironically you were the only person in the thread to remotely take a step toward that path. Even JeQhdMD afforded me the benefit of the doubt by allowing for the possibility that my hacking interest were forensic as oppose to criminal. All the while a legitimate question involving Ubuntu was left unanswered.

The CD is a bootable version of Ubuntu that provides a debugging environment for the coding in the book, it is not a binary version of “confringo” I am salivating to unleash upon the world.
You ended your post by stating “If you need help with Ubuntu” and I restate my original concern. A third of the information in parentheses is a light attempt at humor. 
[B]
New to all things Linux.  

Recently bought "Hacking: The Art of Exploitation" which comes with LiveCD with Linux (Ubuntu) installed.

I'm able to 'boot' Linux for the CD but invariably I get the following message:

"Failed to start the X server (your graphical interface). It is likely that is is not set up correctly. Would you like it to view the X server output to diagnose the problem?"

Here is some info about my computer that might be helpful. 

Dell Inspiron 14R or Dell N4010 

Windows 7 Home Premium (7.2.0)

Generic PnP Monitor 

Intel (R) HD Graphics.
[/B]
**I would appreciate any help I can get in overcoming this hindrance as it seems the Linux gods (coffeecat) are intent on suplexing me into uncle before I get started.**


Though I do not have any illusions that the questions below will get address if the post and/or my account is quarantined I will post them nevertheless.
 [U]
The Fu[/U]
 Fu, your last post in the old thread contained the following:
In order to help, we need to know exactly what you are doing. I cannot tell.

* which release is being used? (I used the release that you recommended that I download 14.04 onto a USB. When I booted it, I opted for “Try Ubuntu” instead of actually downloading it.)

* which sudo commands? (I used the sudo commands you provided when I clicked on the following hyperlinks, “Boot, Backup and Security Questions”  and then on the following page, “Boot Info” under Booting Issues:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update 
 
When I ran this sudo, I got the following feedback: 
 
E: Some index files failed to download. They have been ignored, or old ones used instead.
 
As your guide suggested, I also ran, 
 
sudo apt-get install -y boot-repair && boot-repair
 
When I ran this sudo, I got the following feedback:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package boot-repair)
 
* where is the boot-info URL? It is just a script. (I never got to this part as I was not able to initiate Step 3 in the aforementioned “Boot Info”)
 
_JeQhdMD_
 
Thank you for your suggestion. I want to stick to what the book has provided but if I can’t get this c.d. to work, I guess I’ll have no choice but to pursue alternatives. Additionally, if I understood your question correctly (Are you really trying to boot up an ancient linux CD using the 2.6.20 kernel), the 2.6.20 Ubuntu kernel came on the cd, so I do not have a choice in that regard. I want to give X server problem at least a week and then I’ll move on.  
 
_To all that have read this far:_
 
The original question/problem still stands.

---

