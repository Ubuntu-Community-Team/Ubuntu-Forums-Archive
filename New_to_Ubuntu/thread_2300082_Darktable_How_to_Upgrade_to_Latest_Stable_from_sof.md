---
title: "Darktable: How to Upgrade to Latest Stable from software center version?"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by flyingsolo on 2015-10-23
I have Darktable 1.4.2 installed from the Software Center but I'd like to upgrade to the most recent stable release which is 1.6.9.
First, can I have 2 versions of the software installed simultaneously or must I remove the older version first?

Secondly, I've enabled the PPA for the new version and downloaded the tar.gz file and extracted to the Desktop. To install it, I've been using in a Terminal

./configure

after navigating to the Desktop folder, darktable-1.6.9.
However, I just get an error:

bash: ./configure: No such file or directory

What do you think is my problem/issue? (I've always found installing from non-software center sources somewhat perplexing and no amount of googling has improved my success!)
I thought I had this all going well but clearly I'm missing something crucial in the install process.
Thanks ahead for any help or useful links.

---

### Post by coffeecat on 2015-10-23
General point of principle: if you enable a PPA, there's absolutely no point in downloading a tar.gz source file for the software you enabled the PPA for and compiling it yourself. That way leads to frustration and confusion. PPAs provide ready-compiled deb packages which are installed in the normal way through the Software Centre, or via apt-get, or using Synaptic if that is your preference. Generally, if a PPA version of a piece of software is newer than the regular repo version, it will replace the older version when installed through one of those package managers.

So that members can advise you, post a link to the PPA that you've enabled.

---

### Post by flyingsolo on 2015-10-23
Thanks for the clarification! I've got it fixed now. I think my confusion arose from following the instructions on the Darktable site and then the Github instructions. Between them, they didn't clarify the difference between updating via PPA vs downloading the tar.gz which, as you've explained, are redundant available means to get the software. (probably, they assumed a greater knowledge on the part of users than I had!)

So, I opened Software Sources and added the PPA. Then did a an Update/Install. All went smoothly and now my Darktable is at V 1.6.9.
(I'll just delete the downloaded tar and extracted files as they clearly aren't needed.)

---

