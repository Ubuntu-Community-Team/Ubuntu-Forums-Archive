---
title: "Need a beginners guide to Ubuntu 20.04 questions."
date: 2020-05-03
forum: New to Ubuntu
---

### Post by gaogier1 on 2020-05-03
Hello

i am new here and Linux, not alone Ubuntu. 

so, first question, when turned on, I get “unlock keyring”, it’s not my system password so what is it and how do I stop it?
2nd question, how and where do I find “missing apps, like accessories, Amazon app, passwords and keys and seahorse.
3rd question, my mouse (Logitech m705) has the receiver, but at times the curser is jumpy, the scrolling isn’t smooth how do I fix as it works as normal on my MacBook Pro and iMac (both are old)

more questions as I find them to follow.

---

### Post by CelticWarrior on 2020-05-03
Welcome:


[LIST=1]
[*]The "unlock keyring" appears because you selected the autologin option, something NOT recommended (not even the current Windows allows that easily); the password is the same one you chose for your user during installation; the way to stop it is adopting the recommended practice of login in with a password.
[*](Assuming you're using the standard Ubuntu) You can search for any installed software by clicking the 3x3 dot pattern button at the bottom  of the launcher; type 2/3 letters of the name of what you're trying to find.
[*]Some Logitech wireless mice need additional software in order to be paired and work correctly: [https://askubuntu.com/questions/1093628/logitech-wireless-mouse-m705-not-working-with-ubuntu-18-04-1](https://askubuntu.com/questions/1093628/logitech-wireless-mouse-m705-not-working-with-ubuntu-18-04-1) . Please note that in the answer it is mentioned that Solaar from the github is "better" but that refers to the older version available in the 18.04 release repository. You should try the version already available for 20.04, via the software app or 'sudo apt install solaar' in terminal.
[/LIST]

---

### Post by gaogier1 on 2020-05-03
Thank you for the reply.

1. So when I boot up the computer using ubuntu I have to sign in to stop that &#8220;unlock keyring&#8221;, is it just security?
2. I have looked at the 3x3 dots, where it shows all applications, I have searched for some apps which according to the App Store (that I looked at) are saying it&#8217;s already installed. I have no idea where to look.
3. How do I know I am using the standard or not version?
4. My mouse didn&#8217;t work at all, I then installed solaar last night and it&#8217;s paired, but doesn&#8217;t seem reliable enough to use over the wired mouse. 

new question, would a Bluetooth mouse and keyboard reliable with Ubuntu over the Logitech receiver?

---

### Post by CelticWarrior on 2020-05-03
It's either login with password which in turn automatically unlocks the keyring or type that same password again if the system needs acces to the kwyring (e.g. connecting WiFi to an already saved connection).
Again, you need to type 2 or 3 letter of the name of the app you're looking for.
Ubuntu downloaded from ubuntu.com is the standard version. There are also official derivatives/flavors (e.g. Xubuntu, Kubuntu, Lubuntu, Ubuntu-Budgie, Ubuntu-MATE, etc.) and thousands of other distros based on Ubuntu but usually with different desktop environments so the workflow is different.
You may need to tweak some options in Solaar. Can't help you with that, I don't use Logitech products.
Regarding Bluetooth keyboard and mouse, it depends. Some work great, others not so much.

---

### Post by gaogier1 on 2020-05-03
Hello.

i fully understand that I need to type what app I am looking for, it just simply isn&#8217;t there. - I fixed it by uninstalling and reinstalling. I believe other apps are removed from Ubuntu like amazon.

---

### Post by CelticWarrior on 2020-05-03
Amazon was removed in this latest release.

---

