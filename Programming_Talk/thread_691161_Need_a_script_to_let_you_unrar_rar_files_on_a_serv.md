---
title: "Need a script to let you unrar rar files on a server"
date: 2008-02-08
forum: Programming Talk
---

### Post by samix on 2008-02-08
Well, I started a online arcade and I need to add the swf games to my webserver in a certain directory and then run an SQL command to install them.

Im using rapidleech to tansfer the files to my server, thats working fine. the only problem is the games are in a rar file and cPanel can only unzip zip archives. (to my knowledge).

So, I need a script that I can run on my server to unrar the rar archives and put all the files from those rar's in the same directory as the rar files. If you know what i mean.

The other problem is, the rar files are in formats like "games.part1.rar" and "games.part2.rar"... its about a 300mb rar file split up into 100mb parts... so the script needs to unrar the files from different rar files so it wont get corrupted. Im not sure this is a problem but its worth mentioning.

Can anyone help me? thanks

---

### Post by TameLion on 2008-02-08
Samix,

To run a script you would need shell access, which would mean you could just type the commands to do it anyway. cPanel, to my knowledge, does not give you any kind of console. It might be worth contacting customer support at your web host to ask them to do it for you - if not, you're probably going to have to download locally, unrar, then re-upload.

---

