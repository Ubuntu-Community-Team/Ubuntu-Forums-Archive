---
title: "[php] System return values"
date: 2008-09-26
forum: Programming Talk
---

### Post by Pyro.699 on 2008-09-26
Hello,

Something has me stumped

**In gnome-terminal**
echo Hello World
> Hello World

java test
>Hello World

[B]In PHP
[/B]system("echo Hello World");
>Hello World

system("java\ test");
>

There is no return value when using java scripts? is there a reason for that becasue the java script is beyond simple...

```

public class test{
    public static void main(String[] args){
        System.out.print("Hello World");
    }
}

```

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-09-27
Hey, sorry for the double post but i still havnt found the solution to this problem.

---

### Post by Reiger on 2008-09-27
Try echo [function] ([params]);
Where [function] is your exec/shell_exec/system/w/ever function; and params is the command to be executed...

---

### Post by Pyro.699 on 2008-09-27
So something like this?

```

<?php

function exe($command){
$fh = shell_exec($command);
return $fh;
}

echo exe("java\ test");
?>

```

---

