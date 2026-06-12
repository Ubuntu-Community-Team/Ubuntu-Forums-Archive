---
title: "Why doesn't this command work?"
date: 2012-01-02
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2012-01-02
```
ping -c 20 www.google.co.uk
```

Works fine

```
ping -c 20 www.google.co.uk | grep "36.0"
```

Works fine

```
ping -c 20 www.google.co.uk > ping.txt
```

Works fine

but

```
ping -c 20 www.google.co.uk | grep "36.0" > ping.txt
```

Doesn't work (well not for me!). Seen lots of examples like this offered up. Any suggestions?

---

### Post by ofnuts on 2012-01-02
> **Jose Catre-Vandis said:**
> ```
ping -c 20 www.google.co.uk
```Works fine

```
ping -c 20 www.google.co.uk | grep "36.0"
```Works fine

```
ping -c 20 www.google.co.uk > ping.txt
```Works fine

but

```
ping -c 20 www.google.co.uk | grep "36.0" > ping.txt
```Doesn't work (well not for me!). Seen lots of examples like this offered up. Any suggestions?
What do you mean by "doesn't work"? What are you trying to catch with the "36.0"? part of an address? The response time?

---

### Post by gateway67 on 2012-01-02
It appears that you are attempting to grep for a particular time delay (36.0 ms) for receiving a response to an ICMP request.  How can you be certain that this time will appear in your ping results?

If 36.0 does not appear in the ping results, then obviously the file you are attempting to create will be empty.  Why not experiment with something more predicable to verify that your command construct is valid?  Something like:
```

ping -c 20 www.google.co.uk | grep time > ping.txt

```

---

### Post by fluca1978 on 2012-01-02
This is working fine on Bash:

```
$ ping -c 5 www.google.com | grep icmp > a.txt
```

so either your ping is not presenting 36.0 on output or you are using another shell.

---

### Post by Jose Catre-Vandis on 2012-01-02
By "Works fine" I mean I get output, whether to console or file.

A initial test with ping was giving many 36.0's as the response time but I had the same problem if I chose something else more reliable that was output by ping. Sorry for the confusion.

It's not about the criteria, it's the fact that no data is sent to the file, but I see that it does work for others?

---

### Post by Arndt on 2012-01-02
> **Jose Catre-Vandis said:**
> By "Works fine" I mean I get output, whether to console or file.

A initial test with ping was giving many 36.0's as the response time but I had the same problem if I chose something else more reliable that was output by ping. Sorry for the confusion.

It's not about the criteria, it's the fact that no data is sent to the file, but I see that it does work for others?

This is likely to work like you expect:

```
ping -c 20 www.google.co.uk | grep --line-buffered icmp >ping.txt
```

'grep' normally buffers its output when writing to a file, so even if it has seen three matches, you won't see them in the file yet. The --line-buffered option makes it behave as if it was writing to the terminal.

---

### Post by Jose Catre-Vandis on 2012-01-02
Thanks Arndt that works :)

Just out of interest, if grep is buffering the output, will it "eventually" write to the file or never?

---

### Post by sisco311 on 2012-01-02
Yes it will. For more details check out BashFAQ 009 (link in my signature).

---

### Post by Jose Catre-Vandis on 2012-01-03
Thanks, that's a good link ;)

---

