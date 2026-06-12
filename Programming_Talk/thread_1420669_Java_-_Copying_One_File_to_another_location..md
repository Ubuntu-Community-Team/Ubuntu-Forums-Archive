---
title: "Java - Copying One File to another location."
date: 2010-03-03
forum: Programming Talk
---

### Post by JayKay3000 on 2010-03-03
Hello.

I've been using the code from:

[http://javaxpert.blogspot.com/2008/04/copy-file-or-directory-from-one.html](http://javaxpert.blogspot.com/2008/04/copy-file-or-directory-from-one.html)

to copy a file from one location to another location.

I've slightly modified it to use swing dialogues instead of system.println as they originally did. (not posted)


The problem is really that I can only seem to get it to run off the first file I load so if I load My main file, Java Menu.java  then it works but yet I cannot seem to get it to run from any other part of the program once it's up and running. 


Example of it being run within another files main:

```
 public static void main(String[] args) throws FileNotFoundException,IOException {
    	 
    	 //Starts the instance of FileCopy. (This can not be run like this in another java file once the program is going)
    	
    	   FileCopy.copyFile(new File("G:/Test.txt"), new File("F:/Test1.txt"));

    	//The main program loads. 
       Menu menu = new Menu();
```


For other parts of the program I pre-define them in the Menu file and when I want them I call FileName.setVisible(true);

I have tried calling this file by creating CopyFile test = new CopyFile(); but again that seems to do nothing.

I'm not really sure what I have to add. Perhaps some extra method or loop to get it to activate when I want it.

But i've been fiddling around with it for a while with no luck so if you guys have any ideas it will be appreciated.

---

### Post by raffaele181188 on 2010-03-03
You should post your entire code, so we can help you
Also, it would help if you could upload your whole project directory (if you use an IDE, which is the best choice IMHO)

---

### Post by kahumba on 2010-03-03
Also, that example doesn't use atomic file copy when possible which means if you're trying to move your file from $HOME/Desktop to $HOME/Documents and your file is 1GB it will actually copy the entire 1GB instead of using an atomic copy and thus performing the whole operation in a blink of an eye.
[http://stackoverflow.com/questions/1000183/reliable-file-renameto-alternative-on-windows](http://stackoverflow.com/questions/1000183/reliable-file-renameto-alternative-on-windows)

---

### Post by raffaele181188 on 2010-03-03
> **kahumba said:**
> Also, that example doesn't use atomic file copy when possible which means if you're trying to move your file from $HOME/Desktop to $HOME/Documents and your file is 1GB it will actually copy the entire 1GB instead of using an atomic copy and thus performing the whole operation in a blink of an eye.
[http://stackoverflow.com/questions/1000183/reliable-file-renameto-alternative-on-windows](http://stackoverflow.com/questions/1000183/reliable-file-renameto-alternative-on-windows)
Maybe my English language-bug :D but weren't he speaking about copying a file? Your answer seems more related to moving/renaming. Just wondering, Java is just a hobby of mine :P

---

### Post by kahumba on 2010-03-03
He does, and maybe he only means/needs copying. I thought his app would also need moving files sooner or later as it's closely interrelated to copying.

---

### Post by JayKay3000 on 2010-03-18
Sorry for not getting back on this topic. I put my back out so was out of action for a while.

---

