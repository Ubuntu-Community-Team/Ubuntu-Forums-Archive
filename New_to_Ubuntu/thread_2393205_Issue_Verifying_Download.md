---
title: "Issue Verifying Download"
date: 2018-05-30
forum: New to Ubuntu
---

### Post by hanesdropper on 2018-05-30
I am new to ubuntu and am having trouble verifying my desktop download. I downloaded the desktop iso 18.04 and am walking through the How to Verify Ubuntu Download tutorial: 
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#2](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#2)

I am using Windows 10. I installed bash and did the following step:

md5sum --version
sha256sum --version

which did show me version information, as the tutorial indicated. I then tried the 

gpg --verify SHA256SUMS.gpg SHA256SUMS

step and I got an error message:

gpg --verify SHA256SUMS.gpg SHA256SUMS
gpg: can't open `SHA256SUMS.gpg'
gpg: verify signatures failed: file open error

I figured I didn't download the keys so I did the following:

gpg --keyserver hkp:[I]//keyserver.ubuntu.com --recv-keys 0xFBB75451 0xEFE21092

[/I]This was successful. I tried the verify command again and I got the same error message. I thought I may not have downloaded the checksums and signatures; so I went to 
[http://releases.ubuntu.com/bionic/](http://releases.ubuntu.com/bionic/) 
and downloaded the text files for both sha256sums and sha256sums.gpg 

But I'm still getting the same error message.

The only reasons I can think of for getting the error message is that the text files I downloaded are not saved within the iso file I downloaded, but it seems to be downloaded as a separate disk and it has no room to copy those text files into it. 
Also, the iso downloaded as type Disk File Image... I've downloaded an image file before and I've never experienced it being treated as a separate disk file. 

I don't understand what I'm doing wrong or if I'm just missing something. Again, I am very new to ubuntu and I would really appreciate any help!!

Thank you! :)

NOTE:
I KNOW THERE IS A POST RELATED TO THIS ISSUE:
I have checked the following forum for answers before resorting to posting a new one:
[https://ubuntuforums.org/showthread.php?t=2275427&highlight=verify+signatures+failed%3A+file+open+error](https://ubuntuforums.org/showthread.php?t=2275427&highlight=verify+signatures+failed%3A+file+open+error)

This forum did not help me resolve my issue and I did not find any other forum that helped. If there is one that I didn't find feel free to post the url

---

### Post by Holger_Gehrke on 2018-05-31
The error "can't open `SHA256SUMS.gpg" means gpg can't find the digest-file. The digest (SHA256SUMS.gpg), the checksums (SHA256SUMS) and the iso should all be in the same directory and that directory should be the current working directory. If it isn't, you need to change the working directory using the 'cd'-command. Also check the spelling of the filenames including case (Linux -- as opposed to Windows -- is case-sensitive; I believe the Windows Subsystem for Linux is, too).

Holger

---

### Post by tea for one on 2018-05-31
You can download a checksum utility to run on Windows - here is the link:-

[http://www.nullriver.com/products](http://www.nullriver.com/products) - WinMD5sum

---

