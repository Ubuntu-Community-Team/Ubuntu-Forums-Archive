---
title: "Error from add/rmove application"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by BrandNewSandy on 2008-10-21
[SIZE="3"]I've gotten tis error
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Can anybody tell me how ?? 
Please walk me thru.[/SIZE]

---

### Post by eternalnewbee on 2008-10-21
What were you trying to install?

---

### Post by drakeman007 on 2008-10-21
> **BrandNewSandy said:**
> [SIZE="3"]I've gotten tis error
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Can anybody tell me how ?? 
Please walk me thru.[/SIZE]

You already ran the command 
```
sudo apt-get install -f ??
```

---

### Post by BrandNewSandy on 2008-10-22
I have no idea how. 
Can you help:( a dum?

---

### Post by BrandNewSandy on 2008-10-22
I wanted to install VLC.
I have no idea how to follow the error message, can ou hel?

---

### Post by redseventyseven on 2008-10-22
OK, let's go through this step by step.

> Please check for broken packages with synaptic

Close the "add/remove programs" dialog first, then run the program "Synaptic Package Manager". It does the same sort of job as "Add/Remove Programs" except the programs aren't presented in neat little bundles like in "Add/Remove Programs". Under the "Edit" menu there should be an option to "Fix Broken Packages".

> check the file permissions and correctness of the file '/etc/apt/sources.list'

Open up the file manager and navigate to the folder "/etc/apt" (You may need to click on "File System" in the left-hand pane to get there). Right-click on the file "sources.list" and select "Properties". A dialog box showing the properties of the file should appear. There should be a tab called "Permissions", click this and ensure that the Owner is root and has "Read and write" priveleges.

As for checking the correctness of the file, double click the file to open it in the Text Editor. Each line of the file should either begin with a "#" character (in which case the line is ignored by the program) or look something like:

```
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

Don't worry too much about this step if it's too confusing, it's unlikely that this is the cause of the problem.

Finally...

> reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

OK, before doing this, ensure that Synaptic and Add/remove programs are not open.

For this step you'll need to open up the terminal. Don't worry, it's not as scary as you might imagine!

Type in the following commands:

```
sudo apt-get update
```
and
```
sudo apt-get install -f
```

You may be prompted to enter your password. Don't worry that it doesn't show up when you type your password - this is normal, just type it anyway.

If you get any error messages from any of this lot, or something looks wrong, then post the results to this thread!

Good luck!

---

