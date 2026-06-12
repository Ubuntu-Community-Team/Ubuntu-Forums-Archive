---
title: "PHP IMAP problems"
date: 2005-06-15
forum: Programming Talk
---

### Post by Seth on 2005-06-15
I had a little PHP script I used to run on SuSE. It simply spits out how many mails are in my box.
```
<?php
$mbox = imap_open("{mail.sethkinast.com}INBOX","seth@sethkinast.com", "*****************")
      or die("can't connect: ".imap_last_error());

$check = imap_mailboxmsginfo($mbox);

if($check) {
    print $check->Unread . " / " . $check->Nmsgs;
} else {
    print "error";
}

imap_close($mbox);
?>
```
However, this script doesn't work in Ubuntu. Instead, it asks me for my e-mail password before showing the count. If you notice, the password is included in the call to imap_open. What could change between Ubuntu and SuSE that would force this?

---

