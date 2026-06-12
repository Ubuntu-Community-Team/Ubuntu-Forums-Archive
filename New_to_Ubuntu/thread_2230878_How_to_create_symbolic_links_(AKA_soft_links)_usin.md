---
title: "How to create symbolic links (AKA soft links) using relative pathnames"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by John_Patrick_Mason on 2014-06-21
Hi everybody,

I'm using an introductory book to Linux commands, and I can't seem to understand the example they've given me in the book on how to create symbolic links using relative pathnames.
Right now I know how to create symbolic links using only absolute pathnames like this:
ln -s /home/john/playground/fun dir1/fun-sym
I also know how to create hard links using both relative and absolute pathnames.

Here is the example shown:

```

cd                           #To move to your home directory
mkdir playground          #To create a directory called *playground*
cd playground          #To move to the *playground* directory
mkdir dir1 dir2          #To create two new directories *dir1*, *dir2*
cp /etc/passwd .      #To copy the file *passwd* to the current working directory
mv passwd fun          #To change the name of the file *passwd* to *fun*
ln -s fun fun-sym          #To create a symbolic link pointing to the file *fun* called *fun-sym* (so far so good, this is just like hard links)
ln  -s ../fun dir1/fun-sym    #To create a symbolic link called *fun-sym* in *dir1*  using a relative pathname??? (This is the line that's causing me trouble)
ln -s ../fun dir2/fun-sym      #To create another symbolic link, this time in *dir2*
```

My question is, why wouldn't I be able to just type, "ln -s fun dir1/fun-sym" instead of, "ln -s ../fun dir1/fun-sym" just like we do with hard links using relative pathnames?
Doesn't .. (dot dot) always give the parent directory of the current working directory? So if we are already in */home/john/playground*, wouldn't the directory be changed to the parent directory */home/john*?
Therefore when we type, "ln -s ../fun dir1/fun-sym" aren't we pointing to a nonexistent file named *fun* in *john*? Why can't we just type, "ln -s ./fun dir1/fun-sym" or "ln -s fun dir1/fun-sym" to have our system assume the current working directory, since *fun* is already in the current working directory?

I'd like to specify that I am still new to this.

Thanks for helping me out,

Mason

---

### Post by Impavidus on 2014-06-21
Paths starting with ~ or / are absolute paths, all other paths are relative. All paths mentioned in your example (except for /etc/passwd) are therefore relative paths. The command```
ln -s ../fun dir1/fun-sym
```is a valid command, creating a symlink in ~/playground/dir1/ pointing to ~/playground/fun.

The commands```
ln -s ./fun dir1/fun-sym
#and
ln -s fun dir1/fun-sym
```are equivalent. They create a link named ~/playground/dir1/fun-sym pointing to ~/playground/dir1/fun. That the target of the symlink doesn't exist doesn't matter at this  point, as you're allowed to create links to non-existing targets &#8211; as  long as you don't try to use them. Hard links cannot point to a non-existing file.

The thing to remember is that if you use a relative path for the target of the link, you have to give it relative to the directory where the link is put, not relative to the current directory when you create the link. The path to the link is relative to the current directory whn you call ln. If you create hard links, all paths are relative to the current directory when you create the link.

---

### Post by John_Patrick_Mason on 2014-06-21
OK, as I understand it you can create symbolic links both ways. So if I create a symbolic link in *dir1* by typing, "ln -s fun dir1/fun-sym" and another symbolic link with, "ln -s ../fun dir2/fun-sym" and then try to find out each file's type by typing, "file dir1/fun-sym dir2/fun-sym" how come it tells me that the symlink *fun-sym* in *dir1* is broken and the symlink *fun-sym* in *dir2 *isn't? Is there any functional difference between a broken symbolic link and a "non-broken" symbolic link? How come one symlink is highlighted in red, whereas the other is highlighted in blue? Shouldn't *fun-sym* in *dir1* be called the "non-broken" symlink since it's actually pointing to a file that does exist and have the other symlink *fun-sym* in *dir2* instead be called the broken link since that one isn't pointing to anything that does? The book did point out that hard links can only point to an existing file, and not a directory, within its own filesystem, but it didn't mention that symlinks could point to a nonexisting file. The book's called, "The Linux Command Line: A Complete Introduction," by William E. Shotts, JR. in case others also get confused by this section too.

---

### Post by blaztek on 2014-06-22
John,

In regards to the "ln -s fun dir1/fun-sym" being broken - that is because the dir1/fun-sym symlink is pointing to fun *in the dir1 directory*, which doesn't exist. Personally, for the target parameter of "ln -s", I never use a directory - filename only when doing relative pathnames. Instead, I would do:

[FONT=courier new]cd dir1
ln -s ../fun fun-sym
[/FONT]
To me, that just makes more sense and is a lot less confusing than typing "ln -s ../fun dir1/fun-sym". But that's just me. Plus, doing it like I showed, above, autocomplete (using the TAB key) actually works!

---

### Post by John_Patrick_Mason on 2014-06-22
I think I finally got it. I was having trouble with the syntax. When I was typing:
```
cd playground
ln -s ../fun dir1/fun-sym
```
(continued) I thought .. (dot dot) was relative to the current working directory and not relative to the symlink *fun-sym* that was going to be created. Is that correct?
I also chose that example (ln -s ../fun dir1/fun-sym) because that was the one in the book. Personally I'm not so concerned about how to use symlinks for practical purposes. I have a vague idea of what they can do, but for now I'm only interested in how to create them correctly.

Mason

---

### Post by Impavidus on 2014-06-22
Ah, sorry, I was mistaken. In all those years I use Linux I never made symbolic links in other directories than the current directory. If you set up symlinks the relative path to the target is relative to the directory of the link, not relative to the current directory when you create the link (but the relative path to the link is relative to the current directory when you create the link). I modified my previous post.

---

### Post by John_Patrick_Mason on 2014-06-22
Thanks everybody, that really helped.
I just marked the thread as solved.

Take care,

Mason

---

