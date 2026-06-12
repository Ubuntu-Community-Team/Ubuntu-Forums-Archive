---
title: "how to use kdevelop in ubuntu?"
date: 2008-05-24
forum: Programming Talk
---

### Post by namtien on 2008-05-24
Hi all,
i love ubuntu but am new. i used to use kdevelop with Redhat and now i want to use it with ubuntu but i don't know how/where to start using it (to write c/c++ applications) in ubuntu. counld anyone help me?

---

### Post by LaRoza on 2008-05-24
> **namtien said:**
> Hi all,
i love ubuntu but am new. i used to use kdevelop with Redhat and now i want to use it with ubuntu but i don't know how/where to start using it (to write c/c++ applications) in ubuntu. counld anyone help me?

It should work the same.

I see kdevelop and qdevelop in the repos. Should be a simple install and run. (In GNOME, they will be under the "Programming" menu after they are installed)

```

sudo apt-get update && sudo aptitude install kdevelop build-essential

```

(For general C++ applications, see the sticky on how to use the command line to compile and what package you need)

---

### Post by namtien on 2008-05-24
THanks alot!! i ran the command and got these messages

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "kdevelop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

it seems that nothing done
Please advise me :-)

---

### Post by LaRoza on 2008-05-24
Go to Applications->Add/Remove and change the dropdown list to "All available applications"

Then run the command again.

---

### Post by namtien on 2008-05-24
thanks a lot LaRoza!! it now work fine. I downloaded and installed kdevelop completely!!

---

