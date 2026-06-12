---
title: "Running java app in gui mode on Ubuntu 10/11"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by prashantktyagi on 2012-06-08
Hi All,
I am trying to run java based app on ubuntu 10 in Graphical mode. But I am not able to run in gui mode. 
Is there any other way to achieve this?
I am exporting display to windows machine (using Reflection X).

Any x windows library I am missing here?
I run this code 
<code>
import java.awt.*;
public class ovii{
public static void main(String[] args){
    if (GraphicsEnvironment.isHeadless()){
      System.out.println("Run console mode");
    } else {
        // Start in GUI mode
      System.out.println("Run gui mode");
    }
}
}
</code>

to check wheather gui supported. I am getting "run console mode".

Please help me.

---

