---
title: "imap quota script"
date: 2008-03-26
forum: Programming Talk
---

### Post by yanny on 2008-03-26
Hi,

[PHP]<?php
//show quota
$quota_values = imap_get_quota($conn, "user.yanling")
	or die (imap_last_error());

?>[/PHP]


The error I got is: 

**Bad quota resource list for user.yanling**


I have login with terminal: telnet localhost imap and I did not see "0 capability" so it means the imap server has the 'getquota' capability.... right?

---

