---
title: "active internet connection using java programming"
date: 2006-05-11
forum: Programming Talk
---

### Post by voltage on 2006-05-11
Hi,

do some body tell me how to use Java programming (at x window) to active the internet connection ?

---

### Post by yaaarrrgg on 2006-05-11
I'm not sure I understand what you are asking.  Could you give an example?

---

### Post by sphinx on 2006-05-11
I'm not sure either, however I'm going to take a stab in the dark here as this sounds like problem I had a few years ago.

I once wrote a servlet that ran on a windows box so that you could click on a link in a browser and that computer would initiate a dial up connection to the internet. This way any computer on my home LAN could initiate a dial up connection. This problem was solved in XP later on with the whole connection sharing thing, but anyway, I learned a few things out of doing it. Like it is possible to do some useful things on the command line in windows....

I'm guessing voltage want to know how to write such a thing himself only a desktop based app instead of a servlet based one.

I'll leave the GUI bit as an exercise for the reader, but I'll provide an idea on the bit of Java to actually initiate the connection.

Basicly, the way I would go about it is to use the exec method on the Runtime class. So the first thing you have to do is find out how to do it on the command line. Its been too long since I've done such a thing so I'm going to make up an example that wont work```
#> ifup ppp0 option1 option2
``` So lets pretend thats the commandline command that will innitate a dial up connectin or whatever sort of connection you need to initiate. An example method that could run this command is as follows:
```
public int openInternetConnection() throws IOException, InterruptedException {
        String command = "ifup";
        String args[] = {"ppp0", "option1", "option2"};
        Process pro = Runtime.getRuntime().exec(command,args);
        return pro.waitFor();
}
```

This particular implememtation relies on the exit code to determin if its a success or failure, its a bit more work if you'd like the textual output of the command too for a more helpful error/success message. If I'm on the right track here about what you're after voltage, and you'd like more info about this let me know.

---

### Post by voltage on 2006-05-11
> **sphinx]I'm not sure either, however I'm going to take a stab in the dark here as this sounds like problem I had a few years ago.

I once wrote a servlet that ran on a windows box so that you could click on a link in a browser and that computer would initiate a dial up connection to the internet. This way any computer on my home LAN could initiate a dial up connection. This problem was solved in XP later on with the whole connection sharing thing, but anyway, I learned a few things out of doing it. Like it is possible to do some useful things on the command line in windows....

I'm guessing voltage want to know how to write such a thing himself only a desktop based app instead of a servlet based one.

I'll leave the GUI bit as an exercise for the reader, but I'll provide an idea on the bit of Java to actually initiate the connection.

Basicly, the way I would go about it is to use the exec method on the Runtime class. So the first thing you have to do is find out how to do it on the command line. Its been too long since I've done such a thing so I'm going to make up an example that wont work```
#> ifup ppp0 option1 option2
``` So lets pretend thats the commandline command that will innitate a dial up connectin or whatever sort of connection you need to initiate. An example method that could run this command is as follows:
```
public int openInternetConnection() throws IOException, InterruptedException {
        String command = "ifup" said:**
>  = {"ppp0", "option1", "option2"};
        Process pro = Runtime.getRuntime().exec(command,args);
        return pro.waitFor();
}
```

This particular implememtation relies on the exit code to determin if its a success or failure, its a bit more work if you'd like the textual output of the command too for a more helpful error/success message. If I'm on the right track here about what you're after voltage, and you'd like more info about this let me know.

hi,

thanks for your kindly sugueesion, but what dial up engine i have dial ?? pppd, kppp or diald ? So then can i run the following command "Process pro = Runtime.getRuntime().exec(command,args);" at x window ?

---

### Post by sphinx on 2006-05-16
> **sphinx]```
public int openInternetConnection() throws IOException, InterruptedException {
        String command = "ifup" said:**
>  = {"ppp0", "option1", "option2"};
        Process pro = Runtime.getRuntime().exec(command,args);
        return pro.waitFor();
}
```


I've just realised I've got the wrong method, because I'm working on a related problem myself. The command should be part of the string array.

```
public int openInternetConnection() throws IOException, InterruptedException {
        String args[] = {"ifup", "ppp0", "option1", "option2"};
        Process pro = Runtime.getRuntime().exec(args);
        return pro.waitFor();
}
```

---

### Post by voltage on 2006-05-16
[QUOTE=sphinx]I've just realised I've got the wrong method, because I'm working on a related problem myself. The command should be part of the string array.

```
public int openInternetConnection() throws IOException, InterruptedException {
        String args[] = {"ifup", "ppp0", "option1", "option2"};
        Process pro = Runtime.getRuntime().exec(args);
        return pro.waitFor();
}
```[/QUOTE]

Thank for your info. but may I know which dial up you are using for above procedure ? kppp, pppd or ...other dial up. please advice ...

---

### Post by sphinx on 2006-05-16
[QUOTE=voltage]Thank for your info. but may I know which dial up you are using for above procedure ? kppp, pppd or ...other dial up. please advice ...[/QUOTE]

I havent had a dialup connection for some years now so I can't help you directly. However I did manage to find a wiki page that might be of use.

[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

---

