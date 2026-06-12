---
title: "Mail Ctrl D only works for root user"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by Steve_Watts on 2014-07-23
Hi,
I'm running a VPS with Ubuntu 10.04.4 and trying to send an email using the mail command line program.
This all works lovely for root user but not for my regular login.
I've tracked it down to the control D not being recognized for logged in users and this stops the mail command being sent.
Can anybody help? (I've tried ^D, /dev/null, full stops <<EOF etc etc with no success)

the command I'm trying to run is

echo -e "-------------------- SVN Commit Notification --------------------\r\nRepository: $REPOS\r\nRevision:   $REV\r\nAuthor:     $auth\r\nDate:       $dt\r\n\r\n-----------------------------------------------------------------\r\nLog Message:\r\n-----------------------------------------------------------------\r\n$log\r\n\r\n-----------------------------------------------------------------\r\nChanges:\r\n-----------------------------------------------------------------\r\n$changed\r\n\r\n" | mail -s "$REPOS SVN Commit" [EMAIL="xxxx@xxxx.co.uk"]xxxx@xxxx.co.uk[/EMAIL]

But mail -s "subject title" [EMAIL="xxxx@xxxx.co.uk"]xxxx@xxxx.co.uk[/EMAIL] doesn't work either

It's for a post-commit hook in subversion if that is of any interest.

This is all through PuTTY

I'm a real Linux newbie so be gentle with me
Many Thanks
SWatts

---

