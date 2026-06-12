---
title: "[SOLVED] Error when sending PGP encrypted email from evolution"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by ptn107 on 2008-09-04
For some reason I can't get Evolution to send PGP encrypted emails using my PGP key.  Evolution displays the following message (I'm x'ing out the personal information):
> 
Could not create message.

Because "gpg: using subkey XXXXXXXX instead of primary key XXXXXXXX
gpg: No trust check due to `--trust-model always' option
gpg: [email]xxxxxxxxxxxxxxxx@gmail.com[/email]: skipped: public key not found
gpg: [stdin]: encryption failed: public key not found
", you may need to select different mail options.

It will let me send PGP signed emails but not PGP encrypted.  I've searched and can't find any solution.  Any ideas?

[Running Evolution (2.22.3.1-0ubuntu1) on Ubuntu 8.04.1 amd64]

---

### Post by ptn107 on 2008-09-04
Sweet.  Solved it myself.  The recipients public key was not added [correctly] to my list of trusted keys.

---

