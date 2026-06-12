---
title: "HOWTO: Verify .sig files with a double click"
date: 2009-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Yashiro on 2009-04-08
For some odd reason gpg signature files created with gpg cannot be verified from the shell easily.
This used to work but it seems someone broke the seahorse tool setup later versions of Ubuntu.

.sig files are not associated with any application and thus cannnot be opened with a double-click.

To fix this oversight and restore double click verification:
Open the Properties/Open With dialog for a .sig file.
At the bottom, add the custom action:
seahorse-tool --verify

You can now double click to verify signatures.

---

