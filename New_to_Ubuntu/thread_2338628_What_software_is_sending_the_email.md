---
title: "What software is sending the email"
date: 2016-09-30
forum: New to Ubuntu
---

### Post by Matt_Davies on 2016-09-30
Morning all

I've got a fresh install of ubuntu14.

I've got wordpress installed, and the wp-mail-smtp plugin installed.

If I choose not to use phpmail, what is actually sending the email from the server?

I haven't installed any mail software apart from installing that plugin.

The website states this

"[COLOR=#444444][FONT=Georgia]Reconfigures the wp_mail() function to use SMTP instead of mail() and creates an options page to manage the settings."

[/FONT][/COLOR]https://en-gb.wordpress.org/plugins/wp-mail-smtp/

Any tips or advice greatly appreciated.

---

### Post by TheFu on 2016-09-30
On Unix systems an MTA is normally used to send/receive all email on the box.  Something like exim, postfix, sendmail.  How other tools send email without an MTA is completely lost on me.

---

### Post by buzzingrobot on 2016-09-30
Is WP actually sending mail?  Or are you asking how to get it to send mail without using phpmail?

If you want to send mail, as Fu mentioned, you'll need to set up something to do that and tell WP to use it.

---

### Post by SeijiSensei on 2016-10-01
The only exception to that general advice is if you are using an external SMTP server to handle mail exchange.  Then you would need to configure the WP plugin to connect to the remote server and send its messages there.

---

