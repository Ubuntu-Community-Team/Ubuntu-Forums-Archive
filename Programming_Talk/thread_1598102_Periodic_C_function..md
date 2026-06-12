---
title: "Periodic C function."
date: 2010-10-16
forum: Programming Talk
---

### Post by oopsie on 2010-10-16
I'm still fairly poor at C programming, so sorry if I get the terminology wrong.

What would be the easiest way I could write a programme that had a function that was called 100 times a second?

---

### Post by worksofcraft on 2010-10-16
If nothing else needs to happen you can simply put your program to sleep between calls:
[php]
#include <unistd.h>
#include <stdio.h>

void func() {
	putchar('z'); // shush - I'm sleeping
	fflush(stdout); // force the output out
}

int main() {
	while (1) {
		func();
		usleep(10000); // microseconds
	}
}
[/php]

---

### Post by nvteighen on 2010-10-16
Just to clarify worksofcraft's post: you need to include unistd.h to get usleep(). But, be aware that "unistd" stands for "UNIX Standard", i.e. anything you get from there is not Standard C and will only be available in UNIX and Unix-like OSs.

---

### Post by Some Penguin on 2010-10-16
[http://www.embedded-linux.co.uk/tutorial/periodic_threads]("http://www.embedded-linux.co.uk/tutorial/periodic_threads")

timer_create / timerfd_create will work.

If you really go with usleep(), for better accuracy, you should track the time taken by the function execution and subtract that from the desired sleep period.

---

