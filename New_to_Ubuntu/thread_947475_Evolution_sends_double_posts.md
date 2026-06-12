---
title: "Evolution sends double posts"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by uhappo on 2008-10-14
I have ubuntu on a few machines. On other machines it works like it should, but on my laptop it posts double posts, always.

I have a GMail-account, and I see also those posts in Sent-folder in GMail. I have set Evolution to save send posts in Gmail Sent-folder.

I have set up this Evolution from other machines backup. Is it the problem? This is really annoying thing, I hope this will get sorted out.

---

### Post by Orange_and_Green on 2008-10-14
Hello uhappo :)

An easy way to work around the problem would be making a note of your current Evolution configuration, then renaming your current ~/.evolution directory to .evolution-backup and redo the settings manually.

Good luck :KS

---

### Post by uhappo on 2008-10-14
> **Orange_and_Green said:**
> Hello uhappo :)

An easy way to work around the problem would be making a note of your current Evolution configuration, then renaming your current ~/.evolution directory to .evolution-backup and redo the settings manually.

Good luck :KS

Hi! Thanks alot for suggestions. Still a few Qs:

You mean manually making notes of confs in Evolution? And then ~/.evolution just by Rename to .evolution-backup?

Then fire up evolution and see what happens?

I'll wait an answer and then I'll do what's necessary. Thanks!

---

### Post by Orange_and_Green on 2008-10-15
Hello again :) Sorry for being unclear.

What I mean is, you could make notes of the configuration parameters of your Evolution account(s) (you know, mail servers, login, server settings, news feeds and so on).

The ".evolution" folder in your home directory (it's hidden, press ctrl+H to view it) is where all your personal evolution settings are stored. If you move/rename it, evolution will not find a valid configuration and regenerate a new, "clean" .evolution directory.

You can then set up your account(s) again and see if the problems persist. If you can't manage to set up your accounts again, you can always restore the backup by renaming the backed-up folder back to ".evolution" again.

I hope this explanation is a bit clearer.
Keep us posted, good luck :KS

---

### Post by uhappo on 2008-10-15
Problem solved!

I had somehow changed (can't remember that I had done that) GMail Sent mail-settings. Drafts/Sent-folder was assigned to like User/[GMail]/Sent. When I Reverted those to default Draft/Sent, all is ok now!

Aargh, I made all accounts again from scratch, so there was some unnecessary work, but I know now what to do. I hope my x-perience helps others.

But thanks for your effort man!

---

