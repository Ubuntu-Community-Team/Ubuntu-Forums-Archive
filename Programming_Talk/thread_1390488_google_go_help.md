---
title: "google go help"
date: 2010-01-25
forum: Programming Talk
---

### Post by 65daysofstatic on 2010-01-25
hi,

I'm trying to write a simple program with Go but I'm having problems with input functions.
I want for example ask for a value and assign it to a variable.Like scanf in C: scanf("%d",&i)

65dos

---

### Post by Some Penguin on 2010-01-25
What problem, exactly, are you seeing?

---

### Post by 65daysofstatic on 2010-01-25
I cant find a function to read an integer, thats my problem I'm just starting with Go so I don't know the basic stuff(i have tried reading its documentation but it isnt as friendly as java's one hehe)
I found ReadString and I tried to cast String to integer but I couldn't
so if someone knows how to read an integer or read it as a string and then cast it to int it would be appreciated.

thanks
65dos

---

### Post by Queue29 on 2010-01-26
If you want to do yourself a favor, don't bother learning Go. It is a prime example of how just because famous people are involved with something, doesn't make that something any *good*. Go is syntactically awkward by conventional standards, is not mature or stable, and is by all means slow. It is orders of magnitude slower than C or C++, and offers none of the benefits of using a very high level language like Python or Ruby. And, as you are finding out, it is difficult to accomplish even the most trivial of tasks. For example, want to read a file? Here you go:

```

package main
import (
    "fmt";
    "os";
)
func main()
{
    inName := "file-rw.bin";
    inPerm :=  0666;
    inFile, inErr := os.Open(inName, os.O_RDONLY, inPerm);
    if inErr == nil {
        inBufLen := 16;
        inBuf := make([]byte, inBufLen);
        n, inErr := inFile.Read(inBuf);
        for inErr == nil {
                fmt.Println(n, inBuf[0:n]);
                n, inErr = inFile.Read(inBuf);
        }
    }
    inErr = inFile.Close();
}

```

That is to say nothing of the extremely controversial practice of allowing duck-typing that Go uses instead of the normal object-hierarchy model.

---

