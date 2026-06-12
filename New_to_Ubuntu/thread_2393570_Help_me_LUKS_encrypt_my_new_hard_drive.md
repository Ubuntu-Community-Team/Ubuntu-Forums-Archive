---
title: "Help me LUKS encrypt my new hard drive"
date: 2018-06-05
forum: New to Ubuntu
---

### Post by kaldius on 2018-06-05
Greetings I am asking this here because it wouldn't let me submit a new thread in the other forums. I have recently purchased a new hard drive for my laptop to store media, documents work projects etc.

Now I would like to utilize what is known as the dm-crypt luks encryption for the entire drive to protect the contents from loss or theft. I know Ubuntu provides some tools to encrypt the home folder but I would like to encrypt a whole hard disk that is separate from my Ubuntu installation.

The command is supposed to go something like "cryptsetup options luksFormat --type luks2 device" Now I have read some guides and they are all quite confusing, could someone hold my hand and lead me through the steps with some explanations on how to get full disk encryption using luks on my Ubuntu 18.04? Also I am confused if I should use the default which is luks or the new luks2 which some have suggested.

Your help would be greatly appreciated and I will owe you one favor of your choice at a time of your choosing, thank you =)

---

### Post by mrdc76 on 2018-06-05
You can do this in the Disks app without command line.

---

### Post by kaldius on 2018-06-05
> **mrdc76 said:**
> You can do this in the Disks app without command line.

I wanted to do it with the cli tools themselves so I know its reliable and what is happening, I need advice on how how to formulate the exact command for my disk (/dev/sdb) and which the best options to use are apart from the defaults, like the cipher, hash, key stuff etc.

---

