---
title: "Debugging problem"
date: 2011-03-23
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2011-03-23
Hi,

I am trying to debug a C++ code, that uses threads [but I am debugging a single file/operation/method]. But the debugger does not flow sequentially as it should be. It skips some lines and repeats others, some lines it never reach even there are no conditions that prevent this.

I guess it's threads issue [not sure], I searched the net but I found nothing useful.

Any idea!

Regards,
Ibrahim

---

### Post by Zugzwang on 2011-03-23
Try to:

- Switch off optimizations (-O0 compilation parameters)
- Rebuild the whole project
- Make sure that you never insert/delete a line in some source code file between building the project and running the debugger.

---

### Post by Ibrahim mufeed on 2011-03-23
Hi Zugzwang,

I am using Netbeans, how can I switch off optimizations?

Thank you,

---

### Post by Ibrahim mufeed on 2011-04-01
Yes, It was optimization problem. In Netbeans to disable optimization do the following:
Right click the project node->Code Assistance->Reconfigure project. And add -O0 ;)

Thanks,
Ibrahim

---

