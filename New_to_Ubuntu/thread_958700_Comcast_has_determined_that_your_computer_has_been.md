---
title: "Comcast has determined that your computer has been used to send unsolicited email"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Teasdale on 2008-10-25
I received this from comcast, googled it, and it seems like a lot of people have received this. One guy was told by a comcast tech that EVERYONE is receiving this because they want everyone to change their port from 25 to 465 and 995.

I did a live chat with comcast - I only use webmail, but he determined that Evolution must be the culprit. I've never even opened the Evolution program - I do all my email online. But he had me open it, change it to SSL "with authentication" - which I did. So now I have this email client set up that I really don't want, and I don't see any way to change incoming/outgoing ports.

Supposedly, comcast won't allow me to send any email from that account until I "fix" this "problem," but I just sent a test email from my comcast webmail, and it worked and was received on the other end.

Can I disable or uninstall Evolution? Or is there a way to change the ports? Now that the program is set up, I'm nervous that it could be a security hole.

---

### Post by bpowell2005 on 2008-10-25
> **Teasdale said:**
> I received this from comcast, googled it, and it seems like a lot of people have received this. One guy was told by a comcast tech that EVERYONE is receiving this because they want everyone to change their port from 25 to 465 and 995.

I did a live chat with comcast - I only use webmail, but he determined that Evolution must be the culprit. I've never even opened the Evolution program - I do all my email online. But he had me open it, change it to SSL "with authentication" - which I did. So now I have this email client set up that I really don't want, and I don't see any way to change incoming/outgoing ports.

Supposedly, comcast won't allow me to send any email from that account until I "fix" this "problem," but I just sent a test email from my comcast webmail, and it worked and was received on the other end.

Can I disable or uninstall Evolution? Or is there a way to change the ports? Now that the program is set up, I'm nervous that it could be a security hole.

I don't know of any reason why you couldn't go to the Synaptic package manager, do a search for "Evolution" and then Mark Evolution for complete removal and apply that...It's not required by Ubuntu as far as I know.

That's your email client....if your computer is sending out emails, it could be from an SMTP server (like postfix or something)....but most likely, Comcast is just making some blanket statement.

---

### Post by Kareeser on 2008-10-25
Funny... a level 1 or 2 tech with knowledge of Linux? Unheard of.

In any case, unless evolution is running in the background, it shouldn't be broadcasting itself to the www.

If you've no need for it, you could always uninstall it...

sudo apt-get remove evolution

Don't take my word for this. I do know that evolution is tied to the calendar in the clock, so... who knows what might happen if evolution is uninstalled =P

---

### Post by steveydoteu on 2008-10-25
You can certainly remove the majority of Evolution bar one package. Note, you will lose the functionality of the "About Me" section on the preferences menu.

[http://www.stevey.eu/2008/08/removing-evolution-mail-is-not-dangerous-in-the-slightest/](http://www.stevey.eu/2008/08/removing-evolution-mail-is-not-dangerous-in-the-slightest/)

As I have stated there in the past, it is perfectly safe, and will break no dependencies provided you leave the package [B]evolution-data-server-common.

[/B]> **Kareeser said:**
> Funny... a level 1 or 2 tech with knowledge of Linux? Unheard of.

What world do you live in? A low level tech could quite easily have a knowledge of GNU/Linux. Anyone is quite capable of picking up a CD or an ISO image and giving it a go.

---

### Post by jerome1232 on 2008-10-25
As far as changing ports in evolution it's actually very easy

You just add a colon after the address then type the port number.

mail.address.here:5435

---

### Post by melojo on 2008-10-25
> **Teasdale said:**
> I received this from comcast, googled it, and it seems like a lot of people have received this. One guy was told by a comcast tech that EVERYONE is receiving this because they want everyone to change their port from 25 to 465 and 995.

I did a live chat with comcast - I only use webmail, but he determined that Evolution must be the culprit. I've never even opened the Evolution program - I do all my email online. But he had me open it, change it to SSL "with authentication" - which I did. So now I have this email client set up that I really don't want, and I don't see any way to change incoming/outgoing ports.

Supposedly, comcast won't allow me to send any email from that account until I "fix" this "problem," but I just sent a test email from my comcast webmail, and it worked and was received on the other end.

Can I disable or uninstall Evolution? Or is there a way to change the ports? Now that the program is set up, I'm nervous that it could be a security hole.

> That's your email client....if your computer is sending out emails, it could be from an SMTP server (like postfix or something)....but most likely, Comcast is just making some blanket statement.

If you never even setup an account in evolution it wouldn't now the incoming or outgoing server so how could evolution be the problem. I agree that Comcast is just making a blnket statement

---

### Post by jerome1232 on 2008-10-25
> **melojo said:**
> If you never even setup an account in evolution it wouldn't now the incoming or outgoing server so how could evolution be the problem. I agree that Comcast is just making a blnket statement

I completely agree, the guys on the phones undoubtedly have to follow scripts though.

---

### Post by Teasdale on 2008-10-25
> **Kareeser said:**
> Funny... a level 1 or 2 tech with knowledge of Linux? Unheard of.

Actually, he had no knowledge about Linux. He kept insisting that I had to have *some* kind of email client, so when I did some research and learned that Ubuntu comes with Evolution, he decided it could only be that.

I will probably just remove Evolution. First, I'll try to look into it enough to be sure that it won't disable something I actually need.

---

### Post by Teasdale on 2008-10-25
I went into Synaptic Manager to remove Evolution, and it said it would remove a couple of other things - so I clicked "Okay," and it highlighted those things in bright, bold RED! That was freaky, so I chickened out and didn't remove it.

I opened Evolution and deleted the account I had set up. If the program isn't opened, and it has no email accounts associated with it, can it possibly be used to send spam?

Since I have Ubuntu/Firefox, wouldn't it be unlikely that a virus would be able to get into my PC to do that anyway? Comcast is telling me that it's a virus on my computer that's doing this.

---

### Post by melojo on 2008-10-25
> **Teasdale said:**
> I went into Synaptic Manager to remove Evolution, and it said it would remove a couple of other things - so I clicked "Okay," and it highlighted those things in bright, bold RED! That was freaky, so I chickened out and didn't remove it.

I opened Evolution and deleted the account I had set up. If the program isn't opened, and it has no email accounts associated with it, can it possibly be used to send spam?

Since I have Ubuntu/Firefox, wouldn't it be unlikely that a virus would be able to get into my PC to do that anyway? Comcast is telling me that it's a virus on my computer that's doing this.

I serious doubt that you have a virus!
I have several email accounts and one is through yahoo and i wanted to forward it to my gmail account but yahoo wants money for this.  Gmail allows you to get your email from another server through pop download.  I had to set the ports for this so yahoo wouldn't complain.  This is done strictly through webmail.

Have you done anything like this?

---

### Post by w4ett on 2008-10-26
> **Teasdale said:**
>  One guy was told by a comcast tech that EVERYONE is receiving this because they want everyone to change their port from 25 to 465 and 995.

Seems a bit fishy to me.....I have Comcast, and AFAIK the required port by them is 110. (At least in my area) I use Thunderbird as my Email client, and have had no problems.

I don't usually expect much from them anyway.  When I recently moved here, the installation tech (I use that term loosely) took one look at my computer's desktop, and when he couldn't find the "Start" button, he told me that Comcast service would not work on Linux, and that I would have to install Vista.  :P  What a joke.

---

### Post by doas777 on 2008-10-26
well, here is my advice. take it for what it is.

The tech knew nothing and assumed you had a rooted windows pc, which had been coopted into sending bad emails.

what has likely happened, is that your account have been comprimised, and someone at another IP has been logging in as you and sending bad mails. either that or it is someone spoofing you as sender in the header, but I'm giving the ISP the benifet of the doubt, and assuming that they have verified that the emails were actually sent through their smtp system. 

so what do you do? well start by getting them to assign you a new email account/address and set a strong password on it (>8 char, alpha And numeric, change case, and use a special character).

you can try running chkrootkit, or rkhunter, but you are likely safe on your host. the problem is likely half a world away.

good luck,
Franklin

---

