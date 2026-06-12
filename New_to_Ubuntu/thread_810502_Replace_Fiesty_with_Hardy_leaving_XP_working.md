---
title: "Replace Fiesty with Hardy leaving XP working"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Healey on 2008-05-28
Hi All

I have a laptop which is a Compaq Presario C310 EA which I currently run dual boot with Feisty and Win XP. All works very well but soon Feisty will no longer be supported and I would like to install Hardy Heron in its place. (Gutsy had problems)

I have tried the Hardy Heron live CD and all seems to work as far as I can tell.

I have tried to google this but I just got confused by the responses.

My question is :
As this must happen quite often, what is the official method of removing Feisty installing Hardy whilst not upsetting win Xp as I need to use it occasionally ??

A step by step guide would be great if there is one - I am only a beginner !


Thanks

Healey

---

### Post by rolnics on 2008-05-28
Firstly do you still need any data from your linux install? If not and you have a backup of all the things in windows then the way I would do it is to boot up via the live cd. Double click the install icon on the desktop and when you are faced with the partition screen, I would click manual option. From there you can delete all the existing linux partitions or format just format them.

---

### Post by Healey on 2008-05-28
Hi 

Thanks for your reply - I can back up all my stuff on an external hard drive and the copy back after install.

If I do that will grub be updated at the same time ?? 

I am concerned that grub will be left looking for an older version of ubuntu and therefore fail to boot

Am I correct

Thanks

Healey

---

### Post by kansasnoob on 2008-05-28
Purely as a matter of personal choice I'd use the procedure in this tutorial:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

The only real difference is that you're starting with Feisty instead of Gutsy, So you'd end up with a triple boot .......... Hardy, Feisty, and XP.

Of course I'm assuming that you have enough disc space available to resize your Feisty partition? 10 gb should be plenty to get Hardy up and running (I'd suggest 6 gb minimum).

The greatest benefit to following this procedure is that you'll still have a working Feisty system to use while you work out any issues with Hardy. Then when you have Hardy working great you can just boot the live CD again and use Gparted to delete the Feisty partition(s) and give that space to Hardy or even create a seperate home partition.

---

### Post by artir on 2008-05-28
I would recomend you to do this:
Make the backups, boot from the Hardy's live CD and using the partition editor(System-Administration), erase the Feisty's partition. Then install hardy choosing "install in bigger contiguous empty space or sth like that" The grub will be updated and all happy.
I've done that since dapper and 0 errors.

---

### Post by Healey on 2008-05-28
Hi

Thanks for the replies

I will need to read through the info and then decide which route to follow

Thanks again

Healey

---

### Post by Healey on 2008-05-28
The greatest benefit to following this procedure is that you'll still have a working Feisty system to use while you work out any issues with Hardy. Then when you have Hardy working great you can just boot the live CD again and use Gparted to delete the Feisty partition(s) and give that space to Hardy or even create a seperate home partition.[/QUOTE]

Just a thought - If I do delete Feisty AFTER installing Hardy surely grub will not know about the deleted OS and will fail on the next boot

Will I need to to something to grub before deleting Feisty ??

Thanks

Healey

---

### Post by phr0ze on 2008-05-28
Why not just upgrade from Feisty to Gutsy using the upgrade tool, Then upgrade to Hardy the same way. This will surely leave windows in place and even keep what you have achieved on Feisty. If this method doesn't provide the best results move to the other suggested method.

---

### Post by Healey on 2008-05-28
Hi
Thanks for the reply

I have never tried the "Upgrade" route because of all the bad comments I have heard about it.

Also when I tried the Gutsy live CD on this laptop when it was released it really did not like it !!!  I cant remember what the issues where but it was bad.

So I think the chances of success would be slim !!

Regards

Healey

---

### Post by kansasnoob on 2008-05-28
"Just a thought - If I do delete Feisty AFTER installing Hardy surely grub will not know about the deleted OS and will fail on the next boot

Will I need to to something to grub before deleting Feisty ??"

Since Hardy was installed last Hardy will still boot after you get rid of Feisty and Windows will still show up in the bootloader menu. OTOH, if you should encounter problems with Hardy that you just can't work out (very doubtful), and you'd choose to dump Hardy then you'd first want to edit GRUB to boot Feisty first.

Actually if you're not afraid of losing Feisty following the upgrade path may work quite well for you. Just be sure you get all updates in Feisty before upgrading to Gutsy, and then get all updates in Gutsy before upgrading to Hardy. My luck with upgrades has been about 50/50 .......... half the time it works great, the other half ...... not so much.

---

### Post by Healey on 2008-05-28
Hi
[/quote]   Since Hardy was installed last Hardy will still boot after you get rid of Feisty and Windows will still show up in the bootloader menu. OTOH, if you should encounter problems with Hardy that you just can't work out (very doubtful), and you'd choose to dump Hardy then you'd first want to edit GRUB to boot Feisty first.[/quote]

Thanks For the above - It sounds logical - I need to learn how to edit grub

---

