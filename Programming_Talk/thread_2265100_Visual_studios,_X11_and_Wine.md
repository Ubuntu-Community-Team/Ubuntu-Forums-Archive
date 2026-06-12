---
title: "Visual studios, X11 and Wine"
date: 2015-02-12
forum: Programming Talk
---

### Post by Matthew_Harrop on 2015-02-12
Is it possible to use wine to run Microsoft Visual Studios and then share it over SSH with X11?

---

### Post by Holger_Gehrke on 2015-02-12
In theory yes, but of course there's the problem whether the version of VS you've got works in wine at all before you can even think about X11 forwarding. According to the [AppDB at winehq]("https://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=5&sAction=view&sTitle=View+Developer") most versions of Visual Studio don't work or work with more or less severe trouble. Only the 2005 and 2010 Express Editions are rated "Gold" and "Silver", respectively, everything else is rated "bronze" (it runs, sort of, kinda , ...) or "garbage" (don't try this at home, kids ...).

---

### Post by Matthew_Harrop on 2015-02-12
I suppose there is nothing like trying.

How would I go about sharing a wine application over ssh x11 forwarding?

---

### Post by Holger_Gehrke on 2015-02-13
Just like you'd make any X application run with X11 forwarding. You give the '-X' option (that's capital 'X', 'x' switches forwarding **off**) to ssh and start the application from the command line with 'wine "path/to/program.exe"'. The result should be that VS runs on the ssh server but displays on the ssh client. Obviously, both wine and VS have to be installed on the server for this to work,

---

