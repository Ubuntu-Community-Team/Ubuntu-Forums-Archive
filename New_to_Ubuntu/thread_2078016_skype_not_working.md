---
title: "skype not working"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by flavio_ on 2012-10-29
Hi, I'm using ubuntu 12.10 and my skype was working perfectly, but video image was upside down. 

So, I follow these instructions (for ubuntu 64bit)

[http://ubuntuforums.org/showpost.php?p=8925031&postcount=225](http://ubuntuforums.org/showpost.php?p=8925031&postcount=225)

and now skype is not even open. 

What should I do?

How can I revert what I did?

Hope I can get some help here.

---

### Post by TheMTtakeover on 2012-10-30
> **flavio_ said:**
> Hi, I'm using ubuntu 12.10 and my skype was working perfectly, but video image was upside down. 

So, I follow these instructions (for ubuntu 64bit)

[http://ubuntuforums.org/showpost.php?p=8925031&postcount=225](http://ubuntuforums.org/showpost.php?p=8925031&postcount=225)

and now skype is not even open. 

What should I do?

How can I revert what I did?

Hope I can get some help here.

Did you try un-installing and then re-installing?

---

### Post by flavio_ on 2012-10-30
Yes. A couple of times. And still not working.

---

### Post by flavio_ on 2012-10-30
> **TheMTtakeover said:**
> Did you try un-installing and then re-installing?

Do you have any idea of what should I do?

---

### Post by monkeybrain2012 on 2012-10-30
Go to your home directory and click View > Show Hidden Files (or press ctr +H ) Find the configuration file .Skype and delete it and see if this helps.

---

### Post by flavio_ on 2012-10-30
> **monkeybrain2012 said:**
> Go to your home directory and click View > Show Hidden Files (or press ctr +H ) Find the configuration file .Skype and delete it and see if this helps.

Thanks for the tip, mb; yet, it did not work. I did delete the file and re-installed Skype. Still the same condition. 

Any other hint?

---

### Post by monkeybrain2012 on 2012-10-30
> **flavio_ said:**
> Thanks for the tip, mb; yet, it did not work. I did delete the file and re-installed Skype. Still the same condition. 

Any other hint?


I see that you installed libv4l from the ppa, maybe you need to downgrade it.

Try install ppa-purge and use it to downgrade your libv4l:

```
sudo apt-get install ppa-purge
```when it is installed

```
sudo ppa-purge ppa:libv4l/ppa
```

EDITED: Alternatively, disable the ppa (if you have synaptic install),and then completely remove libv4l, reload synaptic and install it again.

---

### Post by flavio_ on 2012-10-30
> **monkeybrain2012 said:**
> I see that you installed libv4l from the ppa, maybe you need to downgrade it.

Try install ppa-purge and use it to downgrade your libv4l:

```
sudo apt-get install ppa-purge
```

when it is installed

```
sudo ppa-purge ppa:libv4l/ppa
```

Once again, thank you. I successfully installed ppa-purge; and downgraded my libv4l. However, the problem persists. And now, I must day the pc is seems slower than before.

---

### Post by flavio_ on 2012-10-30
> **wsmmwx said:**
> Superb! Generally I never read whole articles but the way you wrote this information is simply amazing and this kept my interest in reading and I enjoyed it.
[Mac Cosmetics Outlet](http://www.maccosmeticsmarkets.com)
[******* Jacket ](http://www.monclerjacketsmart.co.uk)
[Tiffany & Co Jewelry ](http://www.tiffanysandcojewelry.com)
[Karen Millen Outlet ](http://www.karenmillenfr.com)
[Beats Dr Dre  ](http://www.beatby-drdre.com)

Any clue?

---

### Post by monkeybrain2012 on 2012-10-30
Spam.

---

### Post by flavio_ on 2012-10-30
> **monkeybrain2012 said:**
> Spam.

Yes, just realized that. But monkeybrain, do you have any other idea on how to fix it? 

I thought about re-installing 12.10. Is there any option to do that using a few commands on the terminal? 

I appreciate your help.

---

### Post by monkeybrain2012 on 2012-10-30
I just suggested you to downgrade libvl4, did you see my post?

But maybe before you do that,  open the terminal and type 
skype 

and post the error message.

---

### Post by flavio_ on 2012-10-30
> **monkeybrain2012 said:**
> I just suggested you to downgrade libvl4, did you see my post?

But maybe before you do that,  open the terminal and type 
skype 

and post the error message.

Yes. I saw your post. And I did it. But no result.

---

### Post by flavio_ on 2012-10-30
> **flavio_ said:**
> Yes. I saw your post. And I did it. But no result.

Problem solve, Monkey. 

What I did: remove and re-install via terminal. 

apt-get remove skype

apt-get autoremove

I do not know what autoremove is, but it worked for me. 

The video still upside down, but I'll try to solve it later. 

Thanks anyway.

---

### Post by AlexDudko on 2012-10-30
The upside down video is definitely a camera driver issue. I could fix it in Windows by downloading and installing some third-party driver just about a year ago. But in Linux everything was in vain. I couldn't make it show video properly in both (then current versions of) Ubuntu and Fedora.

---

### Post by flavio_ on 2012-10-30
> **AlexDudko said:**
> The upside down video is definitely a camera driver issue. I could fix it in Windows by downloading and installing some third-party driver just about a year ago. But in Linux everything was in vain. I couldn't make it show video properly in both (then current versions of) Ubuntu and Fedora.

But the intriguing fact is that the image (webcam) works perfectly with Cheese; with skype is okay; expect it is upside down.

---

### Post by AlexDudko on 2012-10-30
> **flavio_ said:**
> But the intriguing fact is that the image (webcam) works perfectly with Cheese; with skype is okay; expect it is upside down.

Then it's a different case - I had upside-down image in both Cheese and GoogleTalk plugin for Empathy. There were some instructions to recompile libv4l library but it didn't help.
Skype is a proprietary piece of software, it's not opensource  and it could use its own approach to manipulate video devices.

---

