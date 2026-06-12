---
title: "Custom LiveCD — Skip Install/boot to desktop and run custom app"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by Hamza_Saglam on 2015-07-05
[FONT=arial]Hi folks,

[COLOR=#111111]Following the list of instructions [here]("http://askubuntu.com/questions/48535/how-to-customize-the-ubuntu-live-cd"), I was able to create a LiveCD that I can boot (testing in Virtualbox) but I can't seem to find a way to "boot to desktop", skipping the "Install dialog" ([Screenshot]("http://imgur.com/tqyj0va")). I have to wait until the Install app is loaded and then click on "Try Ubuntu" to finally get to the Desktop.
[/COLOR]
[COLOR=#111111]Essentially I want to boot to desktop and also launch an application that I store somewhere in the filesystem. Can I somehow disable Install app appearing and replace it with an application of my own choosing (that I already store somewhere on the filesystem)?
[/COLOR]
[COLOR=#111111]Thanks.[/COLOR][/FONT]

---

### Post by ajgreeny on 2015-07-05
I think you need to just remove the installer ubiquity from the custom live system.

Or do you still want the ability to install but just do not want the two options at that particular point?

---

