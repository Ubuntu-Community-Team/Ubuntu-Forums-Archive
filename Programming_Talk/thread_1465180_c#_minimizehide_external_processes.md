---
title: "c# minimize/hide external processes"
date: 2010-04-29
forum: Programming Talk
---

### Post by ziuciek on 2010-04-29
Hi, i have a problem: i wrote in c# some code that should open an external process minimized:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;

namespace do_kasacji
{
    class Program
    {
        static void Main(string[] args)
        {
            ProcessStartInfo info = new ProcessStartInfo();
            info.WindowStyle = ProcessWindowStyle.Minimized;
            info.FileName = "notepad";

            using (Process pr = Process.Start(info))
            {
                pr.WaitForExit();
            }
        }
    }
}

```

and it works. However only in Windows system. I need to write a similar code which would run in linux. I use gtk-sharp-2.0 library and i've been searching or the soution but haven't found any.. Could anyone help?

---

