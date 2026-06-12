---
title: "Social Networking Project"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by Evil_chilli on 2011-09-12
Hi All,

Excuse my ignorance but I am an absolute beginner and I have decided to take on a bit of large project but I am lost as to were to even start.

I started by researching and decided to install Elgg to help with the development of the Social network I have in mind.

It required for me to install PHP5.2 / Apache2 / MySQL 5+

So I now have a few questions, which no doubt will seem very basic and rudimentary.

Can I run all of the above packages from my desktop simultaneously or will I have to create a partition/virtual server to run them on?

Any help or guidance would be greatly appreciated since I have not been able to even finish the installation of Elgg.

Thanks

EC

---

### Post by Dangertux on 2011-09-12
You can run them from your desktop, however I recommend setting up a virtual machine if that is a possibility for you.

If you are a beginner it will give you more experience with what goes into maintaining and creating something like that. Plus it makes clean up when you're done a heck of a lot easier. You can just close down the VM and call it a day, and you don't have to worry about securing services running on your desktop machine.

Just my 2 cents.

---

### Post by Evil_chilli on 2011-09-12
> **Dangertux said:**
> You can run them from your desktop, however I recommend setting up a virtual machine if that is a possibility for you.

If you are a beginner it will give you more experience with what goes into maintaining and creating something like that. Plus it makes clean up when you're done a heck of a lot easier. You can just close down the VM and call it a day, and you don't have to worry about securing services running on your desktop machine.

Just my 2 cents.


Cheers dude. saw some of the stuff you've published as well. Any recommendations on articles / sources of info for setting up a VM within  Ubuntu?

---

### Post by haqking on 2011-09-12
> **Evil_chilli said:**
> Cheers dude. saw some of the stuff you've published as well. Any recommendations on articles / sources of info for setting up a VM within  Ubuntu?


Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date)

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

sudo usermod -a -G vboxusers username 

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

You will probably end up going headless eventually and may need something a bit more commercial for your hosting, but for testing this is fine.

Have fun

Regards

haqking

---

### Post by Dangertux on 2011-09-12
There is also always the option of something with more permanence for virtualization. 

Like KVM or xen server (though canonical has dropped support for xen pretty much)

I can give you some more detailed information when I get back to my computer I am on my phone at the moment.

---

### Post by Evil_chilli on 2011-09-17
@dangertux - ye dude any help/info you can provide would be greatly welcome and appreciated.

Thanks

Chilli

---

