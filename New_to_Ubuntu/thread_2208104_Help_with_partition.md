---
title: "Help with partition"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by Buenadriver on 2014-02-26
Need to learn the partition thing. I know how to get into it from dash, but don't what to do after that. My hard drive is 200GB plus and need to expand the Ubuntu portion of it. Don't know what to click on, and then what command to use. Appreciate help.

---

### Post by slickymaster on 2014-02-26
You can boot from a live CD or USB into Ubuntu. Then open the application gparted which will already be present and resize the partitions you want.

---

### Post by Buenadriver on 2014-02-26
Thats the problem, I, don't know the commands after I get to gparted. What to click on and what command to use. Thanks.

---

### Post by Impavidus on 2014-02-26
Maybe the [manual](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition) helps.

What you want is first to shrink some other partition to get some unallocated space and then expand the partition used by Ubuntu. Read the warnings concerning ntfs partitions, if you want to shrink one of those. Some recommend only using Windows tools to resize ntfs partitions.

---

### Post by slickymaster on 2014-02-26
> **Impavidus said:**
> Maybe the [manual]("http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition") helps.

What you want is first to shrink some other partition to get some unallocated space and then expand the partition used by Ubuntu. Read the warnings concerning ntfs partitions, if you want to shrink one of those. Some recommend only using Windows tools to resize ntfs partitions.

+1

Besides that, there's also [GParted partitioning software - Full tutorial]("http://www.dedoimedo.com/computers/gparted.html") and [How to Use Gparted]("http://www.wikihow.com/Use-Gparted"), and both recur to pictures so to make it more accessible to understand the partitioning process using GParted.

---

### Post by Mark Phelps on 2014-02-26
> My hard drive is 200GB plus and need to expand the Ubuntu portion of it. 

Sounds like what you want to do is shrink the non-Ubuntu portion of it, and if that is true, do NOT use GParted to do that.

If you're running Windows Vista, or Win7, or Win8; instead, use only the Windows Disk Management utility to shrink Windows.  Using GParted to do that risks corrupting the Windows filesystem and rendering it unbootable as a result.

---

### Post by nunecas123 on 2014-02-27
That is why I always recommend two partitions when using Windows. Try to make a partition on Windows with Disk Management and save all the files you wish - then, use that to expand Ubuntu's partition by using Gparted.

---

### Post by Buenadriver on 2014-02-27
Ok, Thanks to all. This was what I was looking for.

---

