---
title: "Creating an EXT4 partition with encrypted HOME folder?"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by JessicaTsang on 2013-04-25
Hi there,

I have Ubuntu 12.10 installed, and one of the suggestions that I had was to create an [COLOR=#000000][FONT=verdana]EXT4 partition with encrypted HOME folder

I was wondering if there is a step by step guide or if someone can provide me directions on how to achieve this?

Furthermore, can I assign an Yubikey to provide second authentication with the encrypted home folder?

Thank you[/FONT][/COLOR]

---

### Post by stevesy on 2013-04-25
> **JessicaTsang said:**
> Hi there,

I have Ubuntu 12.10 installed, and one of the suggestions that I had was to create an [COLOR=#000000][FONT=verdana]EXT4 partition with encrypted HOME folder

I was wondering if there is a step by step guide or if someone can provide me directions on how to achieve this?

Furthermore, can I assign an Yubikey to provide second authentication with the encrypted home folder?

Thank you[/FONT][/COLOR]

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/](http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/)

---

### Post by DuckHook on 2013-04-26
Hi JessicaTsang,

stevesy has given excellent links containing howtos for different options. I just wanted to ask you if you want an encrypted /home in the first place.

It has it's good uses and is needed if you are carrying around lots of sensitive data, but like all tools, it has its drawbacks as well. It's biggest drawback for new users is that it if you forget both your encryption passphrase and your login password, it is impossible to retrieve your data. It is unlikely that you will forget your login password, but stranger things have happened. It also constrains you on some admittedly more advanced scenarios, like booting up and logging in from a remote location using ssh.

You might find that the best option is creating a ~/Private directory instead. Most general users don't need to go all the way to a fully encrypted /home. Here is a previous [thread]("http://ubuntuforums.org/showthread.php?p=12514214#post12514214") outlining the benefits/drawbacks.

---

