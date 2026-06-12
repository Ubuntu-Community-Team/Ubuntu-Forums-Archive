---
title: "Using rsync in Lieu of cp/scp/mv"
date: 2012-02-10
forum: Programming Talk
---

### Post by jamesisin on 2012-02-10
I generally prefer to use rsync to move or copy files around my network.  I have been working to get things to work just so when I move from one drive to another on a local machine but I'm curious about my latest arguments.

I want the files to assume the destination permissions in this case and have settled upon -rltDiSm based on my reading of -a and extracting from it those arguments which are not going to undermine this goal (and adding a couple others).

Are there any caveats of which I ought to be cautious using this particular list of arguments?  Is there a better method?  Any thoughts really...

---

### Post by jamesisin on 2012-02-11
Well my above solution doesn't work in conjunction with sudo because then all the files take on root:root instead.  I am seeking a way to force the transfered files to assume the permissions of the target directory.

How can I do this without having to specify the permissions (as from source and force source using -p)?

---

### Post by Khayyam on 2012-02-11
jamesisin ..

Shouldn't this be in 'general'? Anyhow, I'm hard pushed seeing what your trying to achieve with -rltDiSm. Your additons ammount to 'pruning empty dirs' (which I would say are rare, and on some occassions, needed) and getting (possibly) some space savings on sparse files .. "-r recursive, -l copy links, -t preseve times, -D --devices" are provided by --archive (-a), so your cuting, -p preserve permissions, -t preserve times, -g preserve group, and, -o preserve owner. All well and good, but why? I would generally (that is, under most circumstances) want these attributes for any sync I made whether I'm backing-up, mirroring, or what-have-you.

So, in all, I think your cutting out useful switches and adding some whos use are at best debatable.

The good thing about --archive is that syncing it back, or to a new HD, will prove easy, without these flags preserved you have to figure out who owns what, what permissions each file/dir has, etc, etc. Also, 'times' are particularly useful if you're copying anything outside $HOME, they are a means that package managers can verify the packages integrity (tampered binaries would be time changed). If you archive anything from / having permissions, times, group, owner is a requisite. Even with the contents of $HOME they are worth preserving, some files (like ~/.ssh/authorized_keys2) need to be go-rw and, this means that a simple 'chmod -R /home/username' is not enough. Similarly, executables will lose u+x.

Anyhow .. it should be clear that I think --archive is pretty good for most purposes, unless you have some reason that is not clear to me why its not fit for purpose than I'd advise you use it. You can '-aSm' if really need those specific options.

HTH & best ...

---

### Post by Khayyam on 2012-02-11
> **jamesisin said:**
> [...]I am seeking a way to force the transfered files to assume the permissions of the target directory.

Jamesisin ...

I see your second post now. Remeber rsync has to run under some user, and that user has to have permissions to write to the target. So rsync sets it either to UID of the person running, or (with --archive) to those of the current owner:group. To change these to those of the owner:group of the directory it would need to be run as that owner:group. That or use --archive and 'chown -R user:group /path'.

HTH ...

---

### Post by jamesisin on 2012-02-11
This I understand well.  I can use -a and that (by way of preserve and o and g) gets me sourceuser:sourcegroup and source-permissions.  Of course I could specify forceuser:forcegroup and 644 (for example), but what I would like to accomplish is destinationuser:destinationgroup and destination permissions (inherited from the containing folder located at the destination).

Rsync is powerful and can muck things up if I take an action without deep thinking.  For example if I place a file on a user's Desktop (using rsync) I'll have to sudo it to that location.  In so doing the file will either be root:root or me:me depending if I use -a (-p) or not.  *But* this will *also* change the permissions of Desktop so that I have to return ownership of the user's Desktop to the user.  Ugh.

I prefer using rsync for moving things around for a number of reasons, but it would save me a number of other commands (chown and chmod in the cases above) if I could convince rsync to assume the permissions inherited from the destination (which I think is how cp would default or maybe that's the default for mv I forget which).

(I put this in Programming because it's scripting and that's, er, programming-like.  Maybe it would fare better in General.  Dunno.)

---

### Post by Khayyam on 2012-02-12
> **jamesisin said:**
> This I understand well.  I can use -a and that (by way of preserve and o and g) gets me sourceuser:sourcegroup and source-permissions.  Of course I could specify forceuser:forcegroup and 644 (for example), but what I would like to accomplish is destinationuser:destinationgroup and destination permissions (inherited from the containing folder located at the destination).

OK, but root can run rsync under any UID via 'su username -c "rsync -args" .. su "change[s] the effective user id and group id" so "destinationuser:destinationgroup" can be set exactly as required. I thought that would be clear from "rsync sets it [..] to UID of the person running".

The task of assigning rights is for ACL's, rsync just complies with *nix permissioning logic: if the user who runs rsync can write to the directory, then rsync can.

There was a patch to set --owner=OWNER --group=GROUP (see [here]("http://lists.samba.org/archive/rsync/2001-October/000327.html")) but this is way back in 2001. I imagine it didn't make it into later releases as the same can be done by adopting the UID via su, and the option would require root to work correctly so probably they didn't see much use for it.
 
> **jamesisin said:**
> Rsync is powerful and can muck things up if I take an action without deep thinking.  For example if I place a file on a user's Desktop (using rsync) I'll have to sudo it to that location.  In so doing the file will either be root:root or me:me depending if I use -a (-p) or not.  *But* this will *also* change the permissions of Desktop so that I have to return ownership of the user's Desktop to the user.  Ugh.

Not if one runs rysnc under the UID of that user.

> **jamesisin said:**
> I prefer using rsync for moving things around for a number of reasons, but it would save me a number of other commands (chown and chmod in the cases above) if I could convince rsync to assume the permissions inherited from the destination (which I think is how cp would default or maybe that's the default for mv I forget which).

But "to assume the permissions inherited from the destination" requires nothing more than rsync having write permissions to the destination, which comes from the UID:GID of the user running it.

> **jamesisin said:**
> (I put this in Programming because it's scripting and that's, er, programming-like.  Maybe it would fare better in General.  Dunno.)

I see ... it wasn't a quibble, I just though mods were sticklers about this sort of thing.

best .. khay

---

### Post by jamesisin on 2012-02-12
Let us suppose that I have an account (me) and I am going to send a file to a machine (called remote) to the user Tom (tom) and land that file to Tom's Desktop.  How would I adjust this rsync?

```
sudo rsync -rltiSmP /home/me/xfer/file.iso remote:/home/tom/Desktop/
```

---

### Post by Paddy Landau on 2012-02-12
[s]You could use:
```
rsync --owner=tom --group=tom ...
```[/s]
EDIT: The previous item was wrong. Sorry.

It looks as though you could just use copy (cp) or remote copy (scp).

---

### Post by jamesisin on 2012-02-12
Thanks for taking a look.  The thread is about making rsync perform in lieu of cp or scp.  There are good reasons to prefer rsync; for example since cp and scp don't check for file consistency (which rsync does) file corruption is a concern.

---

### Post by Paddy Landau on 2012-02-12
The only thing I can think of is to use rsync without the archive option, running it as the target user and group. However, as you are copying to another machine, you need to know the target user and group IDs; and that same user ID and group ID must exist on the source machine.

Here is what I mean, assuming that your target (Tom) has user ID 1002 and group ID 1002.
```
sudo -u '#1002' -g '#1002' rsync ...
```It's hardly a perfect solution, but experiment to find out whether or not you can make it work.

---

### Post by jamesisin on 2012-02-12
Which is exactly what I'm working to avoid.  It means adding commands to discover the o and g of the target.  It would be convenient if rsync could just detect and apply them automatically when instructed.

---

### Post by Paddy Landau on 2012-02-12
Sorry. I've racked my brains and don't think of anything.

It is possible but, as you say, it may require a little scripting.

---

### Post by Khayyam on 2012-02-12
> **jamesisin said:**
> Let us suppose that I have an account (me) and I am going to send a file to a machine (called remote) to the user Tom (tom) and land that file to Tom's Desktop.  How would I adjust this rsync?

```
sudo rsync -rltiSmP /home/me/xfer/file.iso remote:/home/tom/Desktop/
```

Simply specify 'user@remote'. You must have +rw to '/home/tom/Desktop' so you either must run as root, or provide it with a UID:GID that has +rw. If you, (meaning whatever UID's you have access under) have +rw then having your key in /home/tom/.ssh/authorised_keys2 isn't a problem (you effectively have access to all the files anyhow).

Again, its simply a matter of running rsync under the UID of the user, or ACL's on remote are such that you have +rw (meaning you share a group, and Tom's home is +rw for that group). 

```
% touch ~/test.iso
% rsync -rltiSmPe ssh /home/khayyam/test.iso example@remote:/home/example/
<f+++++++ test.iso
         689 100%    0.00kB/s    0:00:00 (xfer#1, to-check=0/1)
% ssh example@remote "ls -l test.iso"
-rw-r--r-- 1 example example 0 Feb 12 19:34 test.iso
```You've not said how you are authenticating to 'remote' but whatever method, access is a matter of ACL's on 'remote'.

best ...

Ab Scriptum:  some users (tom) may not like you having access, this is normally why you create a share for such things, but as your administrating this machine and have root access then the issue is essentially mute.

---

