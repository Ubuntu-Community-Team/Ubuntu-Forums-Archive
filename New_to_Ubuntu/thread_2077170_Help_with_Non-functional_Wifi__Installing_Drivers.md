---
title: "Help with Non-functional Wifi / Installing Drivers?"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by Lereh on 2012-10-27
I'm new with Linux.  I was hoping someone could help me out.  I've been trying to get my wifi to work.  I'm using an RTL8187 card.  The card doesn't work with Ubuntu 12.10, BT4, BT3, or Fedora 13.  However it works with Windows just fine, with no driver installation necessary.  In Linux, it can pick up the wireless networks in the area.  It has, rarely, also connected, however, it rarely is able to load a page if it does connect, however it has actually loaded a couple of pages throughout this time.

I've not yet been able to figure out how to install the drivers for the card.  That is currently what I'm trying to do.

I have the drivers downloaded, and I can navigate in the terminal to the directory.  But I am stuck as to what to do next.  All the commands I've tried have no effect (lpci | grep Wireless, and others that're similar), or I get errors that I don't know how to resolve (with "make", or "sudo make install", I get an error saying I need to define a target.

I've tried the readmes that were packaged with the drivers.  I don't understand them...  And I've been literally reading forum posts for weeks, now.   Please help.

Would be greatly appreciated.

Thank you so much.  

-- Lereh

=== update === 

I am trying to install drivers for my wifi adapter.

I have the tar.gz file on a usb drive. 

How do I install the drivers?

I understand I could move it to a directory (somehow, not sure how to do that, since it won't let me drag and drop since I don't have permissions, which would mean I'd have to do it in the terminal using sudo.  How do I do that, though?

After I move it to a directory, I use the command "sudo tar jxvf 'filename' to extract it,

then cd 'filename folder'

then sudo make
then sudo make install

Is that correct?  

How do I copy and paste the tar.gz file or the directory since I can't drag and drop since I don't have permissions???

---

