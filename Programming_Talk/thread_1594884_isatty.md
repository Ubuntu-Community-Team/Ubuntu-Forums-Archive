---
title: "isatty"
date: 2010-10-12
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-12
Writing a desktop terminal emulator my shell isn't giving a prompt and the reason (I suspect) is because it thinks my gui terminal is a file and not a terminal.

There is a function called isatty that tells programs when something is a terminal and if I run it from gnome-terminal it returns true, but running it from my own terminal it returns false.

[php]
#include <stdio.h>
#include <unistd.h> // isatty

int main() {
     return !printf(
          "isatty(fileno(stdin))=%d\n",
           isatty(fileno(stdin))
     );
}
[/php]

So I was wondering if anyone knows how to change the attributes of an i/o stream so that claim they ARE a terminal... or perhaps somewhere else I should be posting things like this :confused:

p.s. image attached - look, no prompts from bash and output from ls command one file per line :(

---

### Post by nvteighen on 2010-10-13
You are correct, you have to tell the system that file is a terminal device. AFAIK, what you have to use is the termios API to create a new stdin and a new stdout and then set them as a terminal I/O devices. Take a look at this: [http://en.wikibooks.org/wiki/Serial_Programming:Unix/termios](http://en.wikibooks.org/wiki/Serial_Programming:Unix/termios)

---

### Post by worksofcraft on 2010-10-13
> **nvteighen said:**
> You are correct, you have to tell the system that file is a terminal device. AFAIK, what you have to use is the termios API to create a new stdin and a new stdout and then set them as a terminal I/O devices. Take a look at this: [http://en.wikibooks.org/wiki/Serial_Programming:Unix/termios](http://en.wikibooks.org/wiki/Serial_Programming:Unix/termios)

Thanks for that link :)
Trying to set the attributes that way it simply kept giving me the error that it wasn't a terminal. Luckily your link lead me on to more links and eventually I discovered that Linux implements [master clone device]("http://linux.die.net/man/7/pty") for Unix 98 pseudo terminals, but it's quite confusing how to use it :confused:

For instance [for pts]("http://linux.die.net/man/4/pts") says this: "Data written to the slave is presented on the master descriptor as input. Data written to the master is presented to the slave as input."

Superficially this sounds reasonable, but my I/O was popping out all over the place like the shell prompt from child process appearing in the original terminal that started my app.

Then hang on... :confused: I thought we normally have **separate** file descriptors for stdin and stdout: Thus I would need separate read and write channels surely [-X That doesn't seem to work at all, but I suppose I'm learning loads about Linux :)

p.s. Ok I think I sussed it... need to open separately for read and write at the slave end, but the master terminal can use just one Read-write handle. Now I just have to stop the terminal from reading it's own output... and I see the termios link you mention explains what I need to do when the user resizes their terminal window :)

---

### Post by worksofcraft on 2010-10-13
Summary for anyone arriving here from search engine and anyone else who wants to program their own terminal:
 
[php]
// g++ pseudoterm.cpp
// this code shows practically all system calls you are going to need to make a pseudo terminal.

#define _XOPEN_SOURCE
#include <stdlib.h> // grantpt, unlockpt
#include <fcntl.h> // to set non blocking i/o
#include <stdio.h> // printf
#include <cerrno> // errno
#include <unistd.h> // read/write
#include <sys/ioctl.h> // for setting the terminal window size
#include <signal.h> // catch window size changes
#include <string.h> // strsignal
#include <termios.h> // tcgetattr

/*
Acknowledgements:
	http://en.wikibooks.org/wiki/Serial_Programming:Unix/termios
	http://linux.die.net/man/3/posix_openpt
	http://www.delorie.com/djgpp/doc/libc/libc_495.html
	http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_21.html#SEC330
	... and contributors on http://ubuntuforums.org/showthread.php?t=1594884 and others
*/

int SlaveOut; // File descriptor for the application's output pseudo terminal

// sighandler_t
void sigwinch_handler(int SigNum) {
	printf("window size change Signum=%d, name=%s\n", SigNum, strsignal(SigNum));
	winsize W;
	ioctl(1, TIOCGWINSZ, &W);
	printf("Window size characters W=%d, H=%d", W.ws_row, W.ws_col);
	printf("Window size pixels W=%d, H=%d", W.ws_xpixel, W.ws_ypixel);
}

void sigIO_handler(int SigNum) {
	printf("Async IO Signum=%d, name=%s\n", SigNum, strsignal(SigNum));
	// could do the reads and writes here instead of polling in a loop
}

// pseudo terminals
int main() {
	// open the master clone device giving a File handle (descriptor) for the newly cloned master
	int Fd = posix_openpt(O_RDWR);
	// find the name of the slave device that will look just like a terminal now
	char *Slave = ptsname(Fd);
	printf("Master File Descriptor=%d, Slave name=%s\n", Fd, Slave);
	if (Fd < 0) return printf("errno=%d\n", errno);

	// change slave owner from root to real uid 
	int Fail = grantpt(Fd);
	if (Fail < 0) return printf("grantpt errno=%d\n", errno);

	// allow the slave to be opened
	Fail = unlockpt(Fd);
	if (Fail < 0) return printf("unlockpt errno=%d\n", errno);

	// Now open the slave "terminal" with separate ID's for reading and writing
	int SlaveIn = open(Slave, O_RDONLY);
	printf("SlaveIn=%d\n", SlaveIn);
	if (SlaveIn < 0) return printf("open SlaveIn errno=%d\n", errno);

	SlaveOut = open(Slave, O_WRONLY);
	printf("SlaveOut=%d\n", SlaveOut);
	if (SlaveOut < 0) return printf("open SlaveOut errno=%d\n", errno);

	// verify it is a terminal
	printf("Master isatty=%d\n", isatty(Fd));
	printf("SlaveIn isatty=%d\n", isatty(SlaveIn));
	printf("SlaveOut isatty=%d\n", isatty(SlaveOut));

	// catch window resize events
	// previous value is returned when not ERR thus it can be restored and perhaps chained (when not NULL)
	sighandler_t OldHandler = signal(SIGWINCH, sigwinch_handler);
	printf("old sighandler=%p\n", OldHandler);
	if (OldHandler == SIG_ERR) {
		return printf("errno=%d from signal for SIGWINCH\n", errno);
	}

	OldHandler = signal(SIGIO, sigIO_handler);
	printf("old sighandler=%p\n", OldHandler);
	if (OldHandler == SIG_ERR) {
		return printf("errno=%d from signal for SIGWINCH\n", errno);
	}

	sigset_t SignalMask;
	sigemptyset(&SignalMask); // always returns 0

	// add two signal identifiers to the mask
	Fail = sigaddset(&SignalMask, SIGWINCH);
	if (Fail == -1) return printf("Failed to add SIGWINCH to mask %d\n", errno);
	Fail = sigaddset(&SignalMask, SIGIO);
	if (Fail == -1) return printf("Failed to add SIGIO to mask %d\n", errno);

	// unblock the identified signals
	Fail = sigprocmask(SIG_UNBLOCK, &SignalMask, &SignalMask);
	if (Fail == -1) return printf("Signal unblock failed %d\n", errno);

	// try a resize:
	// Note: signal is only from controlling terminal
	winsize W = { 50, 25, 800, 500 }; // char row, col, pixel row, col
	Fail = ioctl(1, TIOCSWINSZ, &W); // stdout resize
	if (Fail == -1) return printf("Change Master window size failed %d\n", errno);

	// now anything we write to Fd should appear on SlaveIn
	// anything we write on SlaveOut should appear on Fd
	// use non blocking input to avoid hanging if something goes astray
	// non blocking input from the shell
	Fail = fcntl(Fd, F_SETFL, O_NONBLOCK | O_ASYNC);
	if (Fail == -1) return printf("Master non blocking i/o fail %d\n", errno);

	Fail = fcntl(SlaveIn, F_SETFL, O_NONBLOCK  | O_ASYNC);
	if (Fail == -1) return printf("Slave non blocking input fail %d\n", errno);

	// gt terminal attributes, remove the echo, set the new attributes
	termios TcAttribs;
	Fail = tcgetattr(Fd, &TcAttribs);
	if (Fail == -1) return printf("tcgetattr errno=%d\n", errno);
	TcAttribs.c_lflag &= ~(ECHO | ECHONL);
	Fail = tcsetattr(Fd, TCSAFLUSH, &TcAttribs); // flush before change
	if (Fail == -1) return printf("tcsetattr errno=%d\n", errno);

	// I/O loop
	int C; // store what to echo
	do {
		C = getchar();
		if (C == EOF) break;
		// Master writes what you type for the slave to read
		int N = write(Fd, &C, 1);

		char Buf[20];
		// slave tries to read it (note it may not have arrived yet)
		N = read(SlaveIn, Buf, 19);
		if (N > 0) {
			Buf[N] = '\0';
			printf("Slave Rcv=%s\n", Buf);
			// slave replies
			const char Thanx[] = "Thank You :P";
			N = write(SlaveOut, Thanx, sizeof(Thanx));
		}

		// Master tries to read what the slave wrote
		char MasterIn[20];
		N = read(Fd, MasterIn, sizeof(MasterIn));
		if (N > 0) {
			MasterIn[N] = '\0';
			printf("Master Rcv=%s\n", MasterIn);
		}
	} while (C != EOF);

	close(Fd);
	close(SlaveIn);
	close(SlaveOut);
	return !printf("That's all, folks!\n");
}
[/php]

enjoy :P

---

### Post by nvteighen on 2010-10-14
Hm... using your pseudoterm corrupts the terminal after termination. If you want it to work inside a terminal I guess you should reset the terminal's original settings before quitting. Not sure how, but I guess something like saving the settings in a termios structure and then recalling them... Like what ncurses does by using endwin().

---

### Post by worksofcraft on 2010-10-14
> **nvteighen said:**
> Hm... using your pseudoterm corrupts the terminal after termination. If you want it to work inside a terminal I guess you should reset the terminal's original settings before quitting. Not sure how, but I guess something like saving the settings in a termios structure and then recalling them... Like what ncurses does by using endwin().

Yes I noticed that too. The above code is really only a collection of all the system calls I had to find out about... just to save anyone else all the researching if they want to have a go. I still wanted all the diagnostics in the same window and some of the functions can only be applied to the controlling terminal.

Meanwhile I managed to put all that code into a windowed terminal emulator that uses GtkTextView.

p.s. attached file removed and code is now available from launchpad project "biditerm" (bi-directional terminal).

---

