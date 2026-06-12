---
title: "Ruby: How to Get a System Process to Run w/o Waiting for It?"
date: 2007-07-06
forum: Programming Talk
---

### Post by Ubuntist on 2007-07-06
I'm working on a Ruby program which writes CSV files that I read with Gnumeric.  At the end of my program, I have
```
system 'gnumeric filename.csv'
```so that my CSV file will be automatically opened up for viewing.

The problem is, that the Ruby program does not exit until I close Gnumeric.  I've tried both

```
system 'gnumeric filename.csv&'
```and

```
system '(gnumeric filename.csv)'
```to force the command into a subshell, but Ruby still waits.

Anybody got any ideas?

By the way, if there's a better way to view CSV files, I'm all ears....

---

### Post by ButteBlues on 2007-07-06
> **Ubuntist said:**
> I'm working on a Ruby program which writes CSV files that I read with Gnumeric.  At the end of my program, I have
```
system 'gnumeric filename.csv'
```so that my CSV file will be automatically opened up for viewing.

The problem is, that the Ruby program does not exit until I close Gnumeric.  I've tried both

```
system 'gnumeric filename.csv&'
```and

```
system '(gnumeric filename.csv)'
```to force the command into a subshell, but Ruby still waits.

Anybody got any ideas?

By the way, if there's a better way to view CSV files, I'm all ears....
Sounds like you want to use threading.

Run gnumeric in its own thread.

---

### Post by Ubuntist on 2007-07-06
> **ButteBlues said:**
> Sounds like you want to use threading.

Run gnumeric in its own thread.

Ah, threads.  I have just a vague idea about what they are; I guess now's the time to learn. Thanks!

---

### Post by unixhead on 2007-07-06
You may use fork off and die approach, Kernel#fork

---

### Post by Ubuntist on 2007-07-10
Thanks, guys.

I've now tried both

```

Thread.new {system 'gnumeric filename.csv'}
```and
```
fork {system 'gnumeric filename.csv'}

```In both cases, I find that execution the main program continues, which is what I want, but the main program still won't exit until I close the gnumeric session....

---

### Post by mitchellh on 2009-02-10
Sorry to resurrect this very old thread but I'm coming from a google search and while this thread wasn't at all what I was looking for, its a shame to leave it unanswered for future Googlers.

In order to do this you must double fork in ruby:

```

fork do
  fork do
    system 'gnumeric'
  end
end

```

Hope that helps. Again sorry for resurrecting the thread.

---

