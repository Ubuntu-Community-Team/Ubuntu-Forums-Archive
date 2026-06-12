---
title: "ubuntu ask for password on every startup"
date: 2021-04-24
forum: New to Ubuntu
---

### Post by danezeq2 on 2021-04-24
on the first startups i didn't get this message. for some reason it started to show this message. i can hit "cancel" few  times and it disappears and then show up again
while showing this message i can't even the screenshot so i shot with phone.

---

### Post by TheFu on 2021-04-24
Google found this: [https://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot](https://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot)
I've never used the Gnome Keyring, so it isn't mandatory. It may make accessing some local and remote resources easier for point-n-click GUI users.  IDK.

[https://askubuntu.com/questions/32164/what-does-a-keyring-do](https://askubuntu.com/questions/32164/what-does-a-keyring-do) has more background.
[https://ubuntuforums.org/showthread.php?t=2344173&p=13573819](https://ubuntuforums.org/showthread.php?t=2344173&p=13573819)

Because you didn't say which Ubuntu or which release, I'm just throwing links.  Get better help by always providing the release and DE used.

---

### Post by danezeq2 on 2021-04-24
iamsorry iam so new to ubuntu i don't even know how to check the version. my natual habaitat is WINDOWS.
i think its 20. LTS i've just downloaded it a hour ago.

---

### Post by TheFu on 2021-04-24
> **danezeq2 said:**
> iamsorry iam so new to ubuntu i don't even know how to check the version. my natual habaitat is WINDOWS.
i think its 20. LTS i've just downloaded it a hour ago.

I'll let others help. My answers would probably be more confusing for someone that new. Sorry.

There are lots of "how to learn Linux/Ubuntu" questions in these forums. I've seen 3 in the last 2 weeks. Those have lots of very beginner friendly links.  "Ubuntu Desktop Guide" would be a good google search to start.

"20" isn't a complete release, BTW. Need 3 more characters. For someone new - stick with LTS releases only. Don't go for the development releases that happen 4x more often. [https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release)  explains LTS. It is about the support period and that stability is the primary goal, not trying out new software on millions of users.

---

### Post by ActionParsnip on 2021-04-24
Do you use autologin?

---

### Post by danezeq2 on 2021-04-25
i think so. i have choosen the option no to enter password on everystartup on install

---

### Post by grahammechanical on 2021-04-25
Open System Settings and in the left hand column scroll down until you come to About. Click About and you will get information about your installation including OS name. Then click on Users. Is the slider for Automatic login to the left or right? If it is to the left, then we have enter our user name and password every time we log in. That action should avoid the need to unlock the keyring.

I am guessing that if we have automatic login, then we may need to unlock the keyring for certain programs to run. With automatic login the operating system does not know if the person using the computer is authorised to use the computer. What you may be seeing is a security feature preventing anyone from running programs without authorisation.

Even with automatic login set to off the operating system will still ask us to authenticate certain actions. Such as the installation and removal of Linux kernels during the update/upgrade process.

Regards

---

### Post by danezeq2 on 2021-04-25
auto login is checked.
How can i know what program is asking for password authenticate? 
i've just installed ubuntu, i havnt installed any program since then.

---

### Post by CelticWarrior on 2021-04-25
Please disable auto login, "problem solved". That was an is the suggestion.

It's against the "best practices" and it's counter-productive as you just experienced yourself.

---

