---
title: "Go Release 1"
date: 2012-03-29
forum: Programming Talk
---

### Post by nutrapi on 2012-03-29
Now that release 1 is out - thoughts?

---

### Post by nutrapi on 2012-03-29
So far, I've been testing it and it seems like it's going to quickly become my daily usage language over perl.

I'm absolutely thrilled with its speed, available packages, and simplicity.

simple apps in web.go compared to rails (using the built-in development servers in both) fly.

With my simple test of having an application with a default route in each, that accepted any number of parameters (as a single parameter) after the the root url, and printed it out on the page 200 times; with a test of 1000 requests, and 5 concurrent connections, averaged over 5 times each - I saw go performing 9 times faster.

This is oversimplifying everything, and not giving credit where credit is due, but for many of my daily tasks I am switching to go.

---

### Post by nutrapi on 2012-03-29
It's also worth noting, during my tests Go didn't go any higher than 1% cpu usage whereas rails was hitting 50-60%.

I understand that rails isn't the most performing item in the first place - and it offers a ton of features web.go has yet to offer. I would be better suited to pit flask or bottle against web.go...both I won't, because I rarely use those anymore.

I use rails though, and this is my personal use case.

---

### Post by mobilediesel on 2012-03-29
I think their simple insall instructions missed something. I got go installed and ran their simple "hello, world" program to test it. That worked. I tried installing the go tour using:
```
go get code.google.com/p/go-tour/gotour
```
and got:
```
# cd .; hg clone -U https://code.google.com/p/go-tour /usr/local/go/src/pkg/code.google.com/p/go-tour
abort: Permission denied: /usr/local/go/src/pkg/code.google.com/p/go-tour
package code.google.com/p/go-tour/gotour: exit status 255
```
Tried it with sudo and got:
```
sudo: go: command not found
```
I'm guessing permissions problem but can't find anything useful.

---

### Post by satsujinka on 2012-03-30
> **mobilediesel said:**
> I think their simple insall instructions missed something. I got go installed and ran their simple "hello, world" program to test it. That worked. I tried installing the go tour using:
```
go get code.google.com/p/go-tour/gotour
```
and got:
```
# cd .; hg clone -U https://code.google.com/p/go-tour /usr/local/go/src/pkg/code.google.com/p/go-tour
abort: Permission denied: /usr/local/go/src/pkg/code.google.com/p/go-tour
package code.google.com/p/go-tour/gotour: exit status 255
```
Tried it with sudo and got:
```
sudo: go: command not found
```
I'm guessing permissions problem but can't find anything useful.

Why are you installing to /usr/local? That seems to be the source of your problem.

---

### Post by mobilediesel on 2012-03-30
> **satsujinka said:**
> Why are you installing to /usr/local? That seems to be the source of your problem.

The instructions said > The Go binary distributions assume they will be installed in /usr/local/go so I installed it there. I removed it from /usr/local and now have it in $HOME/go and everything works.

Now to actually start learning what I can do with it.

---

### Post by satsujinka on 2012-03-30
Yeah, I'm not sure why that was the instruction. If you want to use /usr/local/go you'll have to set up the global PATH to include it or call it manually.
As so:
```
sudo /usr/local/go/bin/go get ...
```
I find it's easier to put it in my home and modify my personal PATH.

---

### Post by The Cog on 2012-03-30
Actually, I just did
sudo ln -s /usr/local/go/bin/go /usr/local/bin/go
which seems to work for me, although adding it to my path in ~/.bashrc might be a more proper way.

---

### Post by hoboy on 2012-03-31
Does anybody knows a go plugin for eclipse or Netbeans ?
what ide are you using for go programming ?

---

### Post by The Cog on 2012-03-31
I use geany. I wrote some notes for myself on how to make geany do go properly, see below.

> How to set up for language Go:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Copy the standard filetype_extensions.conf to your local config:
cp /usr/share/geany/filetype_extensions.conf ~/.config/geany

Add the extension recognition to ~/.config/geany/filetype_extensions.conf 
by adding this line:
Go=*.go;

Copy the C definition filetypes.c to filedefs/filetypes.Go.conf:
cp /usr/share/geany/filetypes.c ~/.config/geany/filedefs/filetypes.Go.conf



Edit filetypes.Go.conf and change the setting and keywords sections to this:
[settings]
# default extension used when saving files
extension=go
lexer_filetype=C

[keywords]
# all items must be in one line
primary=break case chan const continue default defer else fallthrough for func go goto if import interface map package range return select struct switch type var
secondary=byte int int8 int16 int32 int64 uint uint8 uint16 uint32 uint64 float32 float64 complex64 complex128 uintptr string bool rune error



In the Geany GUI, edit a .go file and in the menu, select Build->Set Build Commands.
Set the compile command to: go build %e.go
Set the execute command to: ./%e



---

