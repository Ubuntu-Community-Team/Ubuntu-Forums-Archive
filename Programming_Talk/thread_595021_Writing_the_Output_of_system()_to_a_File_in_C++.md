---
title: "Writing the Output of system() to a File in C++"
date: 2007-10-28
forum: Programming Talk
---

### Post by startherepodcast on 2007-10-28
Hi,

I am trying to write the output of a system() command in c++ to my computer to get the current uptime. Currently I have the code below which is not working. Could someone please point out what I am doing wrong or suggest an alternative method of doing this.

```
#include <iostream>
#include <stdlib.h>
#include <fstream>

using namespace std;

int main()
{
  ofstream f_handle ( "/tmp/status.xml" );
  f_handle<<"<?xml version=\"1.0\" encoding=\"ISO-8859-1\"?>";
  f_handle<<"<data>";
  f_handle<<"<uptime>";
  system("uptime >> /tmp/status.xml");
  f_handle<<"</uptime>";
  f_handle<<"</data>";
  f_handle.close();
  return 0;
}
```


Thanks...

---

### Post by LaRoza on 2007-10-28
Can you just do ```
system("ls -a > filelist.txt");
```

This just uses the ls command as an example.

---

### Post by startherepodcast on 2007-10-28
Well the command above worked so I decided to try my previous script again but it doesn't work. Do you think it could be I'm try to write to the same file from both my c++ app and the system() command but the file can only be written to from both? If so could you suggest a fix for it.

---

### Post by aks44 on 2007-10-28
Looks like it... Maybe close the ofstream before using system(), and reopen it just after would solve the problem?

---

### Post by startherepodcast on 2007-10-28
It Turns out I have to close the File Handle in C++ before the system() command can save to the file. If anyone knows a more efficient method than closing the file and reopening it then feel free to post.

Thanks For All Your Help

---

### Post by aks44 on 2007-10-28
This works:

```
f_handle << "some data";
f_handle.flush(); // make sure the data is written to the file
system( /*whatever*/ );
f_handle.seekp(0, std::ios::end); // go to the end of file
f_handle << "more data";
```


However as a side note, the output from uptime may not be XML compliant. I guess it would be safer to use an intermediate temporary file, and encode its contents into your own file according to the XML specifications.

---

### Post by startherepodcast on 2007-10-28
Hi,

Thanks for your suggestion aks44, its just what I was looking for. Could you please point me in the right direction for how I might encode the uptime so it meets the xml specification (I only need the amount of time the computer has been powered on).

---

### Post by aks44 on 2007-10-28
> **startherepodcast said:**
> Could you please point me in the right direction for how I might encode the uptime so it meets the xml specification

I just looked at uptime's output and it seems unlikely that it will contain characters that need to be escaped for XML. Sorry about the false alarm I didn't really pay attention to the actual data and gave this advice as a general warning. :)


FWIW to be able to use an arbitrary string as an XML element's text (using plain old string concatenation), you need to escape a few reserved characters so that they don't mess up the structure of the XML document:

< becomes &lt;
> becomes &gt;
& becomes &amp;
" (double quote) becomes &quot;
' (single quote) becomes &apos;


eg. **3 < 5** would become:
**<someTag>3 &lt; 5</someTag>**

---

### Post by startherepodcast on 2007-10-29
Thanks Anyway for the information. That could come in useful along the way.

---

