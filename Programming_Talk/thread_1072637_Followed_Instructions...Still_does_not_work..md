---
title: "Followed Instructions...Still does not work."
date: 2009-02-17
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-17
I followed these instructions but something is wrong. Can someone help please?

---

### Post by Can+~ on 2009-02-17
Could you paste the code of myfirstcode.cpp here? Not as an image.
[SIZE="1"](and how can you watch a screen with everything so big..)[/SIZE]

---

### Post by Leo Dragonheart on 2009-02-17
```
# include <iostream>

using namespace std;

int main ()
{
   cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
   cin.get()

   return 1;
}
```

I didn't realise my screen looked so big. I think my screen looks normal but then again I am use to and have and old old old monitor...

---

### Post by Can+~ on 2009-02-17
```
#include <iostream>

using namespace std;

int main ()
{
   cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
   **cin.get()**

   return 1;
}
```

Ok, look at the code. Now look at the error.

```
#include <iostream>

using namespace std;

int main ()
{
   cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
   cin.get()**;**

   return 0;
}
```

You missed the ";". Oh, and why did you put return 1? return 0 means no execution problems.

---

### Post by Leo Dragonheart on 2009-02-17
ok I see the error thanx. and this is what it had on the screen...

```
 
#include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}

```

That is copied from the example on the screen.

---

### Post by Can+~ on 2009-02-17
> **Leo Dragonheart said:**
> ok I see the error thanx. and this is what it had on the screen...

That is copied from the example on the screen.

Whatever, did it compile?

And since you love posting pics:
[http://img.photobucket.com/albums/v517/CanXp/Screenshots/Screenshot.png](http://img.photobucket.com/albums/v517/CanXp/Screenshots/Screenshot.png)

---

### Post by Leo Dragonheart on 2009-02-17
How do I get my desktop to look like that?

---

### Post by Leo Dragonheart on 2009-02-17
I thought I was suppose to post screen shots to make it clearer what I am trying to explain. Anyway it worked finally and Thank you Very Much Can+~ for putting up with my lack of knowledge in the matter...

```
leo@Illuzionz:~$ cd Practice\ Folder/
leo@Illuzionz:~/Practice Folder$ g++ -Wall "myfirstcode.cpp" -o executable
leo@Illuzionz:~/Practice Folder$ chmod u+x executable
leo@Illuzionz:~/Practice Folder$ ./executable
HEY, you, I'm alive! Oh, and Hello World!



```;-)

```
Upon reaching the end of main, the closing brace, our program will return the value of 0 (and integer, hence why we told main to return an int) to the operating system. This return value is important as it can be used to tell the OS whether our program succeeded or not. A return value of 0 means success and is returned automatically (but only for main, other functions require you to manually return a value), but if we wanted to return something else, such as 1, we would have to do it with a return statement:

 
#include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}

```

This is where I got the return 1; from. I was reading it wrong.

---

### Post by jimi_hendrix on 2009-02-17
> **Can+~ said:**
> Whatever, did it compile?

And since you love posting pics:
[http://img.photobucket.com/albums/v517/CanXp/Screenshots/Screenshot.png](http://img.photobucket.com/albums/v517/CanXp/Screenshots/Screenshot.png)

nice desktop

---

### Post by aszxcv on 2009-02-17
yeah nice desktop

---

### Post by Can+~ on 2009-02-17
> **Leo Dragonheart said:**
> How do I get my desktop to look like that?

For starters, set the right resolution (in my case, 1280x1024).

[LIST]
[*]Here's the background of Sam Javanrouh:
[http://flickr.com/photos/wvs/2773715076/sizes/o/](http://flickr.com/photos/wvs/2773715076/sizes/o/)
[*]The icons are GnomeElephant Marine.
[http://gnome-look.org/content/show.php/Gnome%2BHumanElephant+Savane%2BMarine+?content=75500](http://gnome-look.org/content/show.php/Gnome%2BHumanElephant+Savane%2BMarine+?content=75500)
[*]Theme is Murrina Candido.
[http://www.cimitan.com/murrine/node/128](http://www.cimitan.com/murrine/node/128)
[*]And Emerald white-glass for the borders.
[http://gnome-look.org/content/show.php/WhiteMod?content=64829](http://gnome-look.org/content/show.php/WhiteMod?content=64829)
[/LIST]

---

### Post by Leo Dragonheart on 2009-02-17
> **Can+~ said:**
> For starters, set the right resolution (in my case, 1280x1024).

[LIST]
[*]Here's the background of Sam Javanrouh:
[http://flickr.com/photos/wvs/2773715076/sizes/o/](http://flickr.com/photos/wvs/2773715076/sizes/o/)
[*]The icons are GnomeElephant Marine.
[http://gnome-look.org/content/show.php/Gnome%2BHumanElephant+Savane%2BMarine+?content=75500](http://gnome-look.org/content/show.php/Gnome%2BHumanElephant+Savane%2BMarine+?content=75500)
[*]Theme is Murrina Candido.
[http://www.cimitan.com/murrine/node/128](http://www.cimitan.com/murrine/node/128)
[*]And Emerald white-glass for the borders.
[http://gnome-look.org/content/show.php/WhiteMod?content=64829](http://gnome-look.org/content/show.php/WhiteMod?content=64829)
[/LIST]

Thanx for the info...I will give it a try. ;-)

---

