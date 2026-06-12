---
title: "Not able to follow instructions on DebuggingProgramCrash wiki"
date: 2009-06-24
forum: Repositories &amp; Backports
---

### Post by decoherence on 2009-06-24
The instructions on the page

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

Tell me 
> 
Import the debug symbol archive signing key:

gpg --keyserver keyserver.ubuntu.com --recv-key 428D7C01 5E0577F2
gpg --check-sigs 428D7C01 # signed by key of Martin Pitt
gpg -o - --export 428D7C01 | sudo apt-key add -

When I run the first command I get 

```
gpg: requesting key 428D7C01 from hkp server keyserver.ubuntu.com
gpg: requesting key 5E0577F2 from hkp server keyserver.ubuntu.com
gpgkeys: key 428D7C01 not found on keyserver
gpgkeys: key 5E0577F2 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

It's bad when the instructions for how to submit a bug report don't work.

(of course, you can just ignore the part about the keys and it'll still work. but dammit, warnings aren't cool!)

---

