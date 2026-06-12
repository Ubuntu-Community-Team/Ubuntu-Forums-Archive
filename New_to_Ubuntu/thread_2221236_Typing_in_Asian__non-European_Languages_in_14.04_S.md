---
title: "Typing in Asian / non-European Languages in 14.04: SCIM not working, &amp; IBUS very poor"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by swarup on 2014-05-01
For many years SCIM has been the premier and preferred input method for many who type non-European languages all over the world. And it worked in all the previous distributions of Ubuntu. But there seems to be a preference in making users type with IBUS instead. Both used to be supported, but now in 14.04 only IBUS has support. For the first time, SCIM has not been incorporated and cannot be used. The language packages come in a bundle called m17n, and m17n only works with IBUS now; it does not work with SCIM. Many who want to type in an Asian language are going to be in difficulty in 14.04! I think the Middle Eastern languages will also suffer the same fate. See problem described [here]("http://askubuntu.com/questions/165980/scim-input-method-not-working"). I have filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/scim-m17n/+bug/1312517") for the matter, but it is not getting any attention. 

[SIZE=4]**If anyone knows a solution for getting scim-m17n to work in 14.04, please put your solution on this thread! **[/SIZE] The matter is urgent for those in need of typing non-European languages.

Those who want to type in non-European languages, please express your support on the [bug]("https://bugs.launchpad.net/ubuntu/+source/scim-m17n/+bug/1312517"), that you want it fixed! Just create a login id, and click that you also are having a problem with it.

---

### Post by swarup on 2014-05-01
We've got success! Gunnar Hjalmarsson has provided a patch that resolves the issue. I have a 64-bit system, and it works fine. I can't say about the 32-bit systems, although I expect it should work fine.

Here I am spelling out exactly what you need to do:

Add "ppa:gunnarhj/misc" to your system's Software Sources. Do this by typing "Software & Updates" in the dash and opening the tool by that name. Once it opens, go to the "other sources" tab and click on "add". In the window that opens, paste his PPA, i.e. "ppa:gunnarhj/misc". Once that is done it will ask you to click there to update the online sources. Once that is finished, then open "software updater" from the dash, and update your system. Make sure in Language Support that the keyboard input method system is still set to scim and not ibus. Then log out and log back in, and it'll be good to go.

If you want to directly read from his site, [go the bug]("https://bugs.launchpad.net/ubuntu/+source/scim-m17n/+bug/1312517") I have created on this issue. See Gunnar's post, and go to the link he gives. There you'll find more detail on the matter i.e. just what is in his ppa. But for those who are newb's, the directions I've given above will I think be easier to follow.

Enjoy using scim-m17n!

Regards, Swarup

---

