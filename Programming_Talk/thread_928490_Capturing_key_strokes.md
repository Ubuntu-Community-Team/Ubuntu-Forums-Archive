---
title: "Capturing key strokes"
date: 2008-09-24
forum: Programming Talk
---

### Post by yang on 2008-09-24
I made a post here asking for a program that can measure your typing speed wherever you're typing:

[http://ubuntuforums.org/showthread.php?p=5845614](http://ubuntuforums.org/showthread.php?p=5845614)

I'd also be interested in throwing together a simple program to do this, but I just don't know how to capture keys.  I've been searching for a while, but haven't had luck finding good information or source code on this.  I've also looked at the code for the uberkey keylogger, but it doesn't seem to work for USB keyboards (which is all I use these days).

Thanks in advance for any tips!

---

### Post by dwhitney67 on 2008-09-24
It seems odd that if your interest is timing one's ability to type, that you would be interested in a per-character input.

In high school I took a typewriting class (yes with actual typewriters), and the speed tests involved determining how fast a person could type in a paragraph (or a sentence).  The words-per-minute rate could be determined using a stopwatch and simple arithmetic.

If indeed you want the characters-per-second (or -minute) rate, then take this arithmetic a little further.

---

### Post by yang on 2008-09-24
Of course!  I'd like to display multiple distinct metrics, including wpm.  But I fail to see how anything can be done without grabbing keyboard input events.  And what you said is precisely what a typing speed program would do, no?  Measure the elapsed time, maintain a count of the keystrokes seen....  Unless you were actually suggesting that I manually (by hand) do things like start/stop a stopwatch, perform character counts, etc.  :)

---

### Post by dwhitney67 on 2008-09-24
> **yang said:**
> Of course!  ...
Unless you were actually suggesting that I manually (by hand) do things like start/stop a stopwatch, perform character counts, etc.  :)

Not by hand, but programatically.

For example (in C++):
[PHP]#include <iostream>
#include <ctime>


const std::string paragraph = "This is a test of the Emergency Broadcasting System (EBS).\n"
                              "If this had been a real test, you would have been instructed\n"
                              "to seek shelter and to begin typing furiously on your keyboard.\n";


int main()
{
  std::cout << "Type the following paragraph exactly as it appears below:\n"
            << "---------------------------------------------------------"
            << "\n\n"
            << paragraph
            << "\n"
            << "---------------------------------------------------------"
            << std::endl;

  std::string input;
  std::string userParagraph;

  std::cout << "\n\nPress enter when you are ready to begin the test...";
  getline( std::cin, input );
  std::cout << "\n\n";

  time_t start = time(0);

  for ( unsigned int i = 0; i < 3; ++i )
  {
    getline( std::cin, input );
    userParagraph += (input + "\n");
  }

  time_t finish = time(0);

  std::cout << "\nThe user entered the following paragraph:\n\n"
            << userParagraph
            << std::endl;

  unsigned int secs = (finish - start);
  float rate = paragraph.size() / (float)secs;

  std::cout << "It took the user " << secs << " seconds to complete the exercise." << std::endl;
  std::cout << "This is equivalent to " << rate << " chars/sec" << std::endl;

  return 0;
}[/PHP]

To compile:
```
g++ -Wall -pedantic TypeTest.cpp -o typetest
```

To run:
```
./typetest
```

P.S.  If you are using Ubuntu and do not have the GCC compiler tools installed, run this command:
```
sudo apt-get install build-essential
```

---

### Post by yang on 2008-09-24
I had explicitly stated at the start of my message:

"...wherever you're typing."

With more elaboration on that in the linked post.  I don't want to spend my time typing given text into a given window to measure my typing speed.

---

### Post by yang on 2008-09-24
I've found that I can monitor keyboard events via Xlib, which is fine for my purposes.

---

