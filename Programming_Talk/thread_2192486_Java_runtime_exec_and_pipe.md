---
title: "Java runtime exec and pipe"
date: 2013-12-08
forum: Programming Talk
---

### Post by erotavlas on 2013-12-08
Hi,

I'm newbie of Java and I have a trouble on executing a command of shell where I use a pipe. I read on the web that it is possible to do something like this:
```

String[] cmd = {
"/bin/sh",
"-c",
"ls /etc | grep release"
};

Process p = Runtime.getRuntime().exec(cmd);

```

This works well. If I try something more complex like this
```

ssh  user@ip 'tar -jcf - file1 file2 ' | tar -C /path -jxf -

```
it does not work and I receive the exit code 255.  Do you have any idea?

Thank you

---

### Post by spjackson on 2013-12-08
Please show what you are putting in String[] cmd for this more complex form.

---

### Post by erotavlas on 2013-12-08
I tried this
```

String[] cmd = {
"/bin/sh",
"-c",
"ssh  user@ip 'tar -jcf - file1 file2 ' | tar -C /path -jxf -"
};
Process p = Runtime.getRuntime().exec(cmd);

```

and also this
```

String cmd = "/bin/sh -c ssh  user@ip 'tar -jcf - file1 file2 ' | tar -C /path -jxf -";
Process p = Runtime.getRuntime().exec(cmd);

```
but both the solutions don't work.

---

### Post by spjackson on 2013-12-09
The following works for me using authorized keys; I struggle to guess why it doesn't work for you. Does your command work from the command line? If tar or ssh weren't installed then you'd get an error!
```

import java.io.IOException;

public class Call {
        
    public static void main(String[] args) throws IOException, InterruptedException {

String[] cmd = {
"/bin/sh",
"-c",
"ssh  me@myhost 'tar -jcf - file1 file2 ' | tar -C ./foo -jxf -"
};

        Process proc = Runtime.getRuntime().exec(cmd);
        System.out.print("Exit code: ");
        System.out.println(proc.waitFor());
    }
}

```

---

