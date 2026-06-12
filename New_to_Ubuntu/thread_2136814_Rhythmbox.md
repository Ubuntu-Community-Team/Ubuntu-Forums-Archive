---
title: "Rhythmbox"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by Habanero101 on 2013-04-18
Hi guys,

I'm having some problems with Rhythmbox. It crashes immediately after launch.

I have tried uninstalling and reinstalling by  

sudo apt-get remove rhythmbox

sudo apt-get install rhythmbox

this did not have any impact on my problem.

---

### Post by ajgreeny on 2013-04-18
See what errors you get when you start it from the terminal with the command **rhythmbox**.  That may help us to sort out the problem.

---

### Post by Cheesemill on 2013-04-18
Try removing your Rhythmbox settings directory....
```
rm -rf ~/.local/share/rhythmbox
```

---

### Post by kostkon on 2013-04-18
Also, you could start it in debug mode, i.e. in a terminal give the following command
```
rhythmbox -d
```

---

### Post by Habanero101 on 2013-04-18
> **ajgreeny said:**
> See what errors you get when you start it from the terminal with the command **rhythmbox**.  That may help us to sort out the problem.

I started it in terminal:

rhythmbox

and got:
Floating point exception (core dumped)

---

### Post by Habanero101 on 2013-04-18
> **kostkon said:**
> Also, you could start it in debug mode, i.e. in a terminal give the following command
```
rhythmbox -d
```

started in terminal

rhythmbox -d

got a lot of gibberish, which I think is launch/start up files, ending with:

(20:52:42) [0x88e4fa0] [rhythmdb_process_one_event] rhythmdb.c:2503: processing RHYTHMDB_EVENT_STAT
(20:52:42) [0x88e4fa0] [rhythmdb_process_stat_event] rhythmdb.c:2101: error accessing file:///media/***/V**S/Jennifer_Lopez-Dance_Again_The_Hits-Deluxe_Edition-CD-FLAC-2012-PERFECT/01-jennifer_lopez-dance_again_(feat._pitbull).flac: Couldn't access file:///media/****/V**S/Jennifer_Lopez-Dance_Again_The_Hits-Deluxe_Edition-CD-FLAC-2012-PERFECT/01-jennifer_lopez-dance_again_(feat._pitbull).flac: Error when getting information for file '/media/****/V**S/Jennifer_Lopez-Dance_Again_The_Hits-Deluxe_Edition-CD-FLAC-2012-PERFECT/01-jennifer_lopez-dance_again_(feat._pitbull).flac': No such file or directory
(20:52:42) [0x88e4fa0] [song_update_availability] rhythmdb-song-entry-types.c:170: deleting entry file:///media/****/V**S/Jennifer_Lopez-Dance_Again_The_Hits-Deluxe_Edition-CD-FLAC-2012-PERFECT/01-jennifer_lopez-dance_again_(feat._pitbull).flac; not seen for too long
(20:52:42) [0x88e4fa0] [rhythmdb_entry_delete] rhythmdb.c:3711: deleting entry 0xaef133b8
Floating point exception (core dumped)
:~$

---

### Post by Habanero101 on 2013-04-18
well I'll be a monkey's uncle...

I entered


rm -rf ~/.local/share/rhythmbox
rhythmbox


and it launched successfully!

Thanks guys, I'll put this as solved!

---

### Post by Habanero101 on 2013-04-18
One more thing guys, not even sure you'll read this after I marked it as solved;


~/.local/share/rhythmbox

what is the full path to this?

I was looking for it manually, but I can't find it.

---

### Post by Habanero101 on 2013-04-18
> **Habanero101 said:**
> One more thing guys, not even sure you'll read this after I marked it as solved;


~/.local/share/rhythmbox

what is the full path to this?

I was looking for it manually, but I can't find it.

Nevermind, found it using:

cd ~/.local/share/

ls -d $PWD/*

it is:

/home/user/.local/share/rhythmbox

---

### Post by Elephant454 on 2013-04-19
~ is an abreviation for /home/user. It can be used in any context, at least as far as I know.

---

### Post by Habanero101 on 2013-04-19
thanks, I learnt that yesterday.

---

