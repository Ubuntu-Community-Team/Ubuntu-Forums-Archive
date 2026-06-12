---
title: "[SOLVED] Write-Enable a MyBook External"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by HyperDriven on 2008-10-05
I would like to delete a few files (20gb or so of them all together) from my MyBook 500gb External HD. 

However, when I try to do this, I get this error message:

[B]
Cannot move file to the Deleted Items folder, do you want to delete permanently?

[I]The file "x" cannot be moved to the wastebasket.

Unable to create wastebasket info file: Read-only file system[/I][/B]

The, when I press the 'Delete' button, so as to delete permanently, I get this error:

[b]Error while deleting.

[I]There was an error deleting 'x'.

Error removing file: Read-only file system.[/I][/b]


So, I did a bit of googling and searching on here, and it seems I have to Write-Enable my external. Not a problem, but I don't know how to do it :o

Any help would be greatly appreciated :)

---

### Post by falkTX on 2008-10-05
What format/file system is your HD?

---

### Post by minky311 on 2008-10-05
Have you tried right clicking the hard drive selecting properties and then clicking on the permissions tab. You should be able to add write access there.

---

### Post by HyperDriven on 2008-10-05
I am pretty sure it is Fat-32. Is there any definite way to check?

On properties it says 'Filesystem type: msdos'

---

### Post by HyperDriven on 2008-10-05
> **minky311 said:**
> Have you tried right clicking the hard drive selecting properties and then clicking on the permissions tab. You should be able to add write access there.

Yeah, I have, but it says 'The permissions of MyBook cannot be determined'. 

I suppose if that tab was accessible then I'd be able to change the write permissions with the click of a button...

---

### Post by HyperDriven on 2008-10-05
Ah, I found a way. I changed the permissions of the folders in the external, not the HD itself. 

Thanks to those who offered their help ;)

---

