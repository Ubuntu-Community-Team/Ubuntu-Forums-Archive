---
title: "How to use Ekiga"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by LindaLou on 2008-07-14
Hello All, I am absolutely new to Linux Ubuntu and need some advice/help/information on using Ekiga with voipdiscount.com.  I was using voipdiscount.com with Windows XP for 2.5 years.  The account is still active as I just switched over to Ubuntu 3 days ago. I am desperate to have this application as I use it to phone business associates, vendors and family as the land line rates here in South America are outrageous.  I am in the dark when it comes to Ekiga. I foound this very helpful [http://ubuntuforums.org/showthread.php?t=309218&highlight=set+Ekiga](http://ubuntuforums.org/showthread.php?t=309218&highlight=set+Ekiga)
but I just can't figure out how to make a phone call, add a contact,etc.  :confused: The sip part is baffling to me. I would be sooo grateful for instructions.  [-o<

---

### Post by brian_p on 2008-07-15
> **LindaLou said:**
> I am in the dark when it comes to Ekiga. I foound this very helpful [http://ubuntuforums.org/showthread.php?t=309218&highlight=set+Ekiga](http://ubuntuforums.org/showthread.php?t=309218&highlight=set+Ekiga)
but I just can't figure out how to make a phone call, add a contact,etc.  :confused: The sip part is baffling to me. I would be sooo grateful for instructions.  [-o<

The link you give lays out what to do very clearly so exactly what is your problem? Does ekiga register with VoipDiscount? What do you mean by not being able to make a phone call?

---

### Post by LindaLou on 2008-07-15
I opened Ekiga today and the error message at the bottom of the screen said "Registration failure: forbidden".  I have entered my information correctly so no conflicts there. Neither ekiga.net nor voipdiscount.com registered - both show "registration failed" in the Accounts window. I entered [email]500@ekiga.net[/email] for an echo test - nothing. I have never used a platform such as Ekiga so I am unfamiliar with the "sip" making a phone call.  And, if both Ekiga and voipdiscount failed to register, I'm not able to place a phone call, correct?  How is the registration of both Ekiga and voipdiscount corrected in the accounts?

---

### Post by brian_p on 2008-07-16
> **LindaLou said:**
> And, if both Ekiga and voipdiscount failed to register, I'm not able to place a phone call, correct?  How is the registration of both Ekiga and voipdiscount corrected in the accounts?

You may want to wait for an ekiga expert to come along; I do not use it as I find twinkle suits my basic phone needs. However, the principles are the same.

Not being able to register with either provider could be due be an incorrect setting (e.g username, password, registrar) or a network problem such as NAT. You don't have a firewall lurking about, do you?

It isn't quite correct to think making a call always depends on being registered. As it happens Voipdiscount will happily process a call from you without your being registered. Of course, they expect to see a valid username/password combination sent as well, but it works for me so you could try phoning someone from your Voipdiscount account.

[email]600@voxalot.com[/email] is something else to try. I know that invariably works.

---

### Post by LindaLou on 2008-07-16
I was reading the posts about twinkle and thought, maybe as a backup. And I have doubled check all user names, passwords, etc.  Everything matches. I was thinking of just starting fresh - removing voipdiscount and the put the settings back to default (original) and see what happens.
It's strange though that Ekiga failed to register on the accounts too.
Nope to the firewall.  I haven't had time to set one up yet.  The [email]600@coxalot.com[/email] - what is it exactly?
Thanks for your input - appreciated.  I will continue to surf and see what I come up with.

---

### Post by brian_p on 2008-07-16
> **LindaLou said:**
> I was reading the posts about twinkle and thought, maybe as a backup. And I have doubled check all user names, passwords, etc.  Everything matches. I was thinking of just starting fresh - removing voipdiscount and the put the settings back to default (original) and see what happens.

It won't do any harm to start afresh. Try leaving STUN and outbound proxy blank to begin with. You don't need both anyway.

> The [email]600@coxalot.com[/email] - what is it exactly?

An echo test (N.B. voxalot). Reachable from any unregistered SIP phone.

---

### Post by LindaLou on 2008-07-31
Sorry for the late response - work before Ubuntu! I have tried everything with Ekiga - nothing works.  I was able to get one call out today.  But then the darn thing wouldn't work again - sound card issue: "Could not open audio channel for audio reception.
An error occured while trying to play audio to the soundcard for the audio reception. Please check that your soundcard is not busy and that your driver supports full-duplex.
The audio reception has been disabled."

I have posted the error in launchpag/ekiga. Had a follow email with instructions - " Edition &#8594; Preferences &#8594; Devices &#8594; Audio Devices

    * Select "ALSA" as the audio plugin
    * Select "Default" as output
    * Select "Default" as input

Edition &#8594; Preferences &#8594; General &#8594; Sound Events

    * Select "Default" as alternate device output
*Disable pulse audio>Exit Ekiga.
Open a terminal, type:
"pasuspender -- ekiga"
(without quotes)"

Didnt work. In fact when I entered the phrase in the terminal the response "command cannot be found" was returned. I am waiting for another response there.  Very strange about the sound card error:
I had nothing running (i.e. music)

---

