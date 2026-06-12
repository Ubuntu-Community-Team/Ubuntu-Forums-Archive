---
title: "HELP NEEDED: bash parsing of C return values"
date: 2007-03-03
forum: Programming Talk
---

### Post by majoridiot on 2007-03-03
i'm running in circles trying to get a bash script to correctly parse return values (error code) of a
C routine:

C routine is called from an init script (run as root) and it returns either 0, 1, or 2- as an error 
code- to be parsed and acted upon by the calling script.

if i run the calling/parsing function of the bash script as a stand-alone script, it works perfectly...
however, if the *exact* same code is run from inside the larger init script itself, it chokes on return
values greater than 0 and does nothing at all.

i've tried returning the values back from the C routine using both return X and exit(x), but it does
not seem to make a difference.

here's the bash function- you can see how absolutely simple i've pared it down to, in an effort
to suss the problem:

```
call_c() {
  /usr/bin/c_routine
# store the return code
  ERR=$?
# test echo it
  echo $ERR
	if [ $ERR -eq "1" ]; then
		echo 'error 1"
	elif [ $ERR -eq "2" ]; then
		echo 'error 2' 		
	elif [ $ERR -eq "0" ]; then
                echo 'no errors'
        else	
		echo 'bad error returned' 				
	fi
return
}
```

if the return is "0", then the echo statement before the if chain prints, the error correctly
echoes after the if and the rest of the script continues on with its business.  if the value is 1 
or 2, the echo before the if chain fails, as do the echos inside the if chain and the script stops
instead of continuing on.

i know the c routine works fine, as it returns 0, 1 or 2 without fail, and that this bash function
*should* work, because it does if run stand-alone with nothing more than a call to the
function.

i'm sure i'm either missing something small or doing something incorrectly- but i can't seem to
find any indication of what that might be in my bash and c references.

could someone be kind enough to help an idiot out?

thanks! :D

---

### Post by s1ightcrazed on 2007-03-03
Have you tried running the c_routine in the background with a sleep before the ifs? 

I'm wondering if the c_routine is not returning control back to the shell unless it exits sucessfully (exit 0). It sounds like the shell is acting as if the routine is FAILING if it does anything other than exit 0, and the script comes to a halt at that point. As a test (and assuming that your c_routine executes in under a few seconds) I would call it like:

```
call_c() {
  /usr/bin/c_routine &
# pause and wait for the c_routine to finish
  sleep 5
# store the return code
  ERR=$?
# test echo it
  echo $ERR
	case $ERR in
                1)
		echo 'error 1" ;;
                2)
		echo 'error 2' ;; 		
                0)
                echo 'no errors' ;;
                *)
		echo 'bad error returned' ;; 				
	esac
return
}
```

Of course, I'm partial to case over multiple ifs, but to each his own. :-)

---

### Post by majoridiot on 2007-03-03
yeah... i converted the case to if's along the way to make it a simple as possible.  it was originally
a case.

there's no problem with the C routine that i know of... run from the command line, it returns the
correct code(s) and run from a simple script it works fine as well.  i tried your sleep suggestion, 
but no good- same result.

i also tried substituting the following for the c function call:

```
TEST=$(call_c)$?
```

thinking that might make the return stick to the variable, but again, no go.  works fine for 0, but
not 1 or 2.   this one has me stumped.

thanks for the suggestion, tho!

---

### Post by s1ightcrazed on 2007-03-03
I still think it's something to do with process forking - the fork is never finishing and the rest of the script ends up just waiting. Any chance you could send me the c_routine so that I could have a go at it? 

Also, did you notice that I ran the routine in the background? You mentioned the sleep, just wanted to be sure you saw the '&' after the call to the c_routine. 

does the initial echo of $ERR actually show anything other than 0, or is it not even getting this far unless the exit IS 0?

---

### Post by yabbadabbadont on 2007-03-03
You are trying to use a numerical comparison operator with non-numerical literal value...

Try changing: if [ $ERR -eq "1" ]; then

To: if [ $ERR -eq 1 ]; then

---

### Post by s1ightcrazed on 2007-03-03
I don't think it's the if statement seeing as how the case failed too. 

good catch though - could also use ==

I did find something additional (thank you google), and it DOES appear more likely that the exit status is the issue. Anything other than 0 indicates to bash a failure of some kind, and it just refuses to continue. 

Instead of doing /usr/bin/c_routine &, try /usr/bin/c_routine ; 

The ; tells bash to move onto the next line regardless if the c_routine completes successfully or not. I would keep the sleep statement though, just to give the c_routine time to finish.

---

### Post by majoridiot on 2007-03-04
i REALLY appreciate the quick answers, guys... unfortunately it's still no go.

after trying your suggestions and googling myself silly (short trip), i'm giving up for the night
before my head explodes.

none of the myriad of changes i tried did anything positive, including taking that entire function
out of the script and replacing it with a call to a test script (which is just a cut and paste of the 
same function and which works from command-line)-- but still no go.  i always wind up with a 
return of 0- even with no case or if's... just an echo of $? directly after the call and then an
exit 0 to stop it dead.

leading me to believe there's something in the bigger script screwing up the works.  dunno what it 
could be, as this function should be one of the only things executed.  i'll have to take a closer 
look...

EDIT: ok, i lied... or more accurately, couldn't leave it alone.  i did some more poking around and
fail to find any reference to returning and being able to manipulate *specific* non-zero values- it 
appears to be 0 for no error or !=0 for error... even though 1 & 2 make it through from a command 
line call.  

anyone know if this is indeed accurate?

if need be, i can do the error handling in the c portion, i was leaving it to BASH to facilitate only
one compile of the major portion whilst tweaking.

thanks again for the quick replies!  this is actually for part the mythtv guides here on our community
docs.

---

### Post by Mr. C. on 2007-03-04
$? is ALWAYS valid, and is the return status of the previous command.  ALWAYS.  It is the return value from the wait(2) (or its variants) system call.

Keep in mind:

man bash:

       The return value of a simple command is its exit status,  or  128+n  if
       the command is terminated by signal n.

As other's have noted, use =, not eq in your test.

Istead of echo, use:

  printf '%x' $?

This allows you to distinuish >127 unprintable ASCII (which to you would like like NULL output from echo).

Whenever you echo back a value as a debug aid, use quotes to see NULL values, as in:

$ echo "ret: '$?'"  
ret: '0'

Otherwise, its difficult to distinguish one or more spaces from NULL.

MrC

---

### Post by Mr. C. on 2007-03-04
> **majoridiot said:**
> 
EDIT: ok, i lied... or more accurately, couldn't leave it alone.  i did some more poking around and
fail to find any reference to returning and being able to manipulate *specific* non-zero values- it 
appears to be 0 for no error or !=0 for error... even though 1 & 2 make it through from a command 
line call.  



A good programmer never quits!  :-)

The standard UNIX/POSIX/libc calling conventions require a return 0 for success, and non-zero for failure.  You may use various non-zero return values to indicate various reasons of failure.  See man diff for example.

MrC

---

### Post by majoridiot on 2007-03-04
thanks loads for that excellent info, C... it's pointed me in a direction and now i can sleep to tackle
it fresh tomorrow.

i had switched from = to -eq in one of dozens of iterations of never-ending changes, but i will go
back to the way it should have been to begin with.  

i'm likely over-complicating it.  gotta sleep.

---

### Post by s1ightcrazed on 2007-03-04
OK - fresh start this morning, so I decided to recreate your little issue. 

I coded a 2 line c program. All it does is a printf and then an exit(1). Compiled it as test_routine. 

I then created a bash script that looks like this:

```
#!/bin/bash
call_c() {
	./test_routine
	echo $?
	return
}

echo "Calling test_routine"
call_c
echo "This is the next line in the script"
exit 0
```

So, just as you did, I have a function that will call the c program and try to read the exit status. And damn it if the thing doesn't work. In fact, I can't get it to fail. Am I missing something from what you were trying to do?

I'm still thinking that this has something to do with process forking, but I want to be able to prove it.

---

### Post by majoridiot on 2007-03-04
a quick post before i find some coffee and a hot shower...

ok, the main() of the C code in question is this:

```
int main() {

    raw1394handle_t handle;	// our firewire handle...
    int port = 0;		// port 0
    int node = 1;		// node 1 is default for 62xx (?)
    
    handle = raw1394_new_handle_on_port(port);	// get a new handle and bind it to our port
    
    if (!handle)		// if no handle is returned, there's a problem
    	return 1;		// exit with handle error
            
    if (!fix_broadcast(handle, node))    // try the fix 
        return 2;			 // failed, exit with priming error    
    
// primed and ready, release the firewire handle and exit with no error
	raw1394_destroy_handle(handle);
        return 0;
}
```
     
it's to prime a firewire connection with a cable stb.  you run this from the command line, it returns
0, 1 or 2 correctly- it has never failed to return with the correct code in error situations.  the
best test to do this with is when the firewire is unavailable to the user (permission-wise) and
is the fastest way to check it- it returns the error in less than a second.

the script (sh, not bash but same/same in this case) looks like this up to the point of failure:

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/mythbackend
NAME="mythbackend"
DESC="MythTV server"

test -x $DAEMON || exit 0

set -e

USER=mythtv
RUNDIR=/var/run/mythtv
ARGS="--daemon --logfile /var/log/mythtv/mythbackend.log --pidfile $RUNDIR/$NAME.pid"
EXTRA_ARGS=""
NICE=0
STAMP=$(/bin/date +%F\ %T)
FIREWIRE=/dev/raw1394

prime_firewire() {
echo 'priming...'

#TEST=$(myth_prime;)$?
#/usr/bin/myth_prime ;
/usr/bin/myth_prime & 
sleep 30
TEST=$?
echo $TEST

#case $TEST in
#               1)
#		echo 'error 1" ;;
#               2)
#		echo 'error 2' ;; 		
#               0)
#                echo 'no errors' ;;
#               *)
#		echo 'bad error returned' ;; 				
#	esac
return
}
# check the status of priming
#        if [ $TEST -eq 1 ]; then
#                echo $STAMP '    ERROR: unable to obtain firewire handle!'
#        elif [ $TEST -eq 2 ]; then
#                echo $STAMP '    ERROR: failed to prime firewire!'
#        elif [ $TEST -eq 0 ]; then
#                echo $STAMP '    firewire primed.'
#        else
#		echo "error"
#        fi
if [ -f /etc/default/mythtv-backend ]; then
  . /etc/default/mythtv-backend
fi

ARGS="$ARGS $EXTRA_ARGS"

mkdir -p $RUNDIR
chown -R $USER $RUNDIR


case "$1" in
  start)
	if test -e $RUNDIR/$NAME.pid ; then
		echo "mythbackend already running, use restart instead."
	else
    prime_firewire
... continues
```

as you can see, it's a mess from everything tried... but the simple fact is that i can't seem to 
simply echo $? from the return, let alone parse it in any way.  the 'sleep' statement has been
anwhere from 1 to 60, but as i said, i don't think the fork is hanging, as the handle error should
be returned immediately, and is from command-line testing.

holla back if you have any thoughts... i need coffee. :confused:

---

### Post by Mr. C. on 2007-03-04
This works just fine.

```
$cat c.c
main(int argc, char *argv[]) {
    int ret = atoi(argv[1]);
    exit (ret);
}

$cc c.c
$cat doit
#!/bin/bash

call_c() {
        ./a.out $1
        echo "  ret: '$?'";
        return
}

echo First
call_c 0

echo Second
call_c 1

$ doit
First
        ret: '0'
Second
        ret: '1'


```

If this were failing as indicated, the entire system would be a mess.  This has nothing to do with forking.

Starting a job in the background, as given in the earlier example by slightlycrazed :
```

 /usr/bin/c_routine &

```
will ALWAYS return 0 (success) if the shell successfully started the process.  The shell will NOT wait for an exit status from the background process, unless you call wait.

MrC

---

### Post by Mr. C. on 2007-03-04
```
/usr/bin/myth_prime & 
sleep 30
TEST=$?
echo $TEST

```

This will never work.  There are two problems here:

a) as indicated in my previous post, a job run in the background will always return a 0 value.
b) your $? assignment is getting the return value of sleep.  $? is ALWAYS the status of the *previous* command.

MrC

---

### Post by majoridiot on 2007-03-04
> **Mr. C. said:**
> ```
/usr/bin/myth_prime & 
sleep 30
TEST=$?
echo $TEST

```

This will never work.  There are two problems here:

a) as indicated in my previous post, a job run in the background will always return a 0 value.
b) your $? assignment is getting the return value of sleep.  $? is ALWAYS the status of the *previous* command.

MrC

yes... i recognized this *before* i tired it, but tried anyway, as it always irks me when advice
is offered and ignored... plus, it aint workin the way i thought it should, so i could have been 
wrong about that too.

i'm about half a mug of coffee from digging back into this.  i really appreciate the help.

kinda frustrating to be done in by simple bash with my extensive background in 9900 assembler.
i guess that's what happens when you thumb yer nose at the programming gods and take a
decade-and-a-half sabbatical. ;)

---

### Post by Mr. C. on 2007-03-04
Understood.

A lesson learned long ago... when the system seems broke, dig deeper to find out what *I* am missing.

MrC

---

### Post by majoridiot on 2007-03-04
ok... another round of major testing, and it seems that *something* in the C code is causing the
hang-up.  it runs fine from the command line or fine from another bash script calling it, but chokes
when called from the init script.

for test, i did:

bash script /etc/init.d/backtest (test replacement for the acual init script i'm working with):
```
#!/bin/bash
/home/mythtv/primer/test
echo "script rtn is '$?'";
exit 0
```

the "test" script that calls is:
```
#!/bin/bash
/usr/bin/myth_prime
TEST=$?
echo "C rtn is $TEST";
exit $TEST
```

running "backtest" fails- reporting 0

running "test" from command line returns correct values!

additionally, i tried a simple sub for "myth_prime":

```
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main() {

int rtnval=2;
    printf("return is %d\n", rtnval);
    exit (rtnval);
}
```

running "test" from the command line returns 2 as it should as it also now does when called 
from /etc/init.d/backtest.

dunno if there is some sort of context switch or if the C code is mucking up the environment
or something else that i'm unaware of.  i've looked the code over closely and don't see anything-
but then again, i'm not sure what i'm looking for.

other than the return error, the only obvious difference between running the C code from
command line or from the init script (even the simple one above), is that it seems to take
considerably longer.  from CLI, it returns error 1 immediately- but it takes 10-15 secs when
launched from the init script.

hehe... no qualms admitting my idiocy here, guys.  what am i missing?

c source attached, in case.

---

### Post by Mr. C. on 2007-03-04
Majoridiot,

(i'm not sure I like addressing someone like that!).


I'll make my earlier hint a little stronger... give up the approach the the unix/libc runtime is broken, or that there are magic context switch elves.  The system works.  Once you accept that, you'll say... "there's an error in *my* program, and I have to debug it to find the error".

Ok, with that out of the way.  Its time for you to learn to use a debugger and single step through your code to see what's going on, line-by-line.  Compile with -g and start it up with gdb, and start walking though it verifying that everything is executing exactly as you expect.

That your program takes 1 second when you run it, but takes significantly longer when invoked via shell script is indicating something fishy; but it has nothing to do with the shell and error code returns, nor that the program was invoked by a shell v. command line.  They will be the exact same.  Things that come to mind... different PATHs mean different programs may be started.  Aliases in your shell may mask which program is *really* invoked.  A different environment run via command line v. shell script can produce different results for errant programs, as the code traipses all over the stack.

Put a sleep(30) in your C program, and start up via shell script.  Ensure that the program that actually is running is the one you think is running.  Then attach a debugger to the live process and see what's going on.  This shouldn't take more than a few minutes.

See what you find.
MrC

---

### Post by majoridiot on 2007-03-04
> **Mr. C. said:**
> Majoridiot,

(i'm not sure I like addressing someone like that!)

no worries... ;)

> **Mr. C. said:**
> The system works.  Once you accept that, you'll say... "there's an error in *my* program, and I have to debug it to find the error".

not a doubt in my mind that it's something i'm doing... i didn't think for a second that i had found
a long-lurking bug.

i was just breaking out by gdb and debugging references to try and suss this.  i'm *very* new to
this whole environment... so there's a lot to learn.  i'll see where i can get with the debugger.

thanks VERY MUCH for the help.  it is appreciated. :D

---

### Post by majoridiot on 2007-03-04
problem solved, i believe... and what it came down to was- yup, you guessed it.  idiocy.  hours
and hours spent trying to find a bug ***that wasn't a bug!***

for those keeping track at home... and anyone else that can learn from finding your stupid mistake
using the toolz given-

i couldn't seem to attach gdb to the running process as it kept giving me an error i didn't feel 
like spending another hour googling, so i used gcov to see what was executing.  when run 
from the CLI, the resulting trace files showed it executed the dozen or less instructions it 
should have before failing...

but when examined after launching it from the init script, it showed *hundreds* of iterations.

so then the idiot sussed it- the init script the C code is launched from is run as root, which
means it has all the permissions necessary to to what the C code was attempting- so it indeed
was returning 0 accurately- there was no error.  launching that code by:

```
su - <intended_user> -c "<executable>"
```

results, of course, in the desired behavior- it errors when it should.

also, the second failure was the *set -e* instruction at the head of the init file i was inserting
this into... returning meaningful errors as i wanted killed it.  commenting it out allows the script
to continue as desired.  that was overlooked of course, as how could four letters and a dash
make any real difference? ;)

aint learning great?

moving onward to finish this up...

**thanks to everyone- especially you, C!**

encouragement is always helpful... and this will benefit fellow ubuntu-ers (or is it -ites?) wanting
a stable firewire connection with their mythtv setup.

of course, this only means i'll return with even more Qs as i get further into working with C...
so you've been warned.

(but not tonight- i promise) :D

---

### Post by Mr. C. on 2007-03-04
You're welcome - glad you found it!

And the lesson leared???   ALWAYS examine return codes from ALL system calls, functions, and ALWAYS generate some form if diagnostic (syslog, print to STDERR, etc.).  A permissions problem should be detected as soon as an open(2), stat(2), or whatever call fails.

Best of Luck!
MrC

---

### Post by majoridiot on 2007-03-04
agreed!

ironic, tho that permission checks i was performing, were  being confused by the wrong user
doing the check!

lesson #2, always be aware of what "user" is actually executing each of your functions, etc.

---

