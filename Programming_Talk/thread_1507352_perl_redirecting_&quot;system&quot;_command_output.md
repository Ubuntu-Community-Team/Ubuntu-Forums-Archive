---
title: "perl: redirecting &quot;system&quot; command output to file"
date: 2010-06-11
forum: Programming Talk
---

### Post by steve_c on 2010-06-11
I have a program where I'm using Parallel::ForkManager to help parallelize a section of code. It has a main process and no more than 8 child processes at a time (if I'm using ForkManager right). During the child processes it calls an external program that takes some time to execute and a fair amount of memory (hence why I'm trying to limit the number of simultaneous processes).

At first during the child threads, in my naivety I was using exec() to call the external program. That obviously created another, unattached child process, which then allowed its parent to finish quickly, then opening up one of the 8 slots for the next job, and so on, without giving the external program time to finish. This quickly ate all my RAM and locked up the machine.

So now I'm using system() to call the external program, and it *seems* to be working, but with a catch. I need to redirect the output from the external program to a log file. For some reason this worked fine with exec() but is not working with system(). I know that the other output files are being created, but not the redirected output. So it seems that I'm just not understanding something about how to properly use perl's system() command. Any thoughts?

Here is the external command:
```
system "$commandPath/$command $path/$configFile > $path/output.$i &";
```

Thanks for any help.

---

### Post by dv3500ea on 2010-06-11
> **steve_c said:**
> I have a program where I'm using Parallel::ForkManager to help parallelize a section of code. It has a main process and no more than 8 child processes at a time (if I'm using ForkManager right). During the child processes it calls an external program that takes some time to execute and a fair amount of memory (hence why I'm trying to limit the number of simultaneous processes).

At first during the child threads, in my naivety I was using exec() to call the external program. That obviously created another, unattached child process, which then allowed its parent to finish quickly, then opening up one of the 8 slots for the next job, and so on, without giving the external program time to finish. This quickly ate all my RAM and locked up the machine.

So now I'm using system() to call the external program, and it *seems* to be working, but with a catch. I need to redirect the output from the external program to a log file. For some reason this worked fine with exec() but is not working with system(). I know that the other output files are being created, but not the redirected output. So it seems that I'm just not understanding something about how to properly use perl's system() command. Any thoughts?

Here is the external command:
```
system "$commandPath/$command $path/$configFile > $path/output.$i &";
```

Thanks for any help.
The system command executes text as if you were typing it into the terminal. The only possible problem I can see with your code is the use of shell redirection to a file AND using the '&' to run in the background. 

You could use threads and pipes to execute each external command:

```
[color=#008000]**use**[/color] threads;

[color=#008000]**my**[/color] [color=#19177C]@THREADS[/color] [color=#666666]=[/color] ();

[color=#008000]**sub **[/color][color=#0000FF]run_parallel[/color] {
	[color=#008000]**my**[/color] [color=#19177C]%opts[/color] [color=#666666]=[/color] [color=#19177C]@_[/color];
	[color=#008000]push[/color]([color=#19177C]@THREADS[/color], threads [color=#666666]->[/color] create([color=#008000]**sub **[/color]{
			[color=#008000]**my**[/color] ([color=#19177C]$commandPath[/color], [color=#19177C]$command[/color], [color=#19177C]$path[/color], [color=#19177C]$configFile[/color], [color=#19177C]$i[/color]) [color=#666666]=[/color] (
				[color=#19177C]$opts[/color]{[color=#BA2121]'commandPath'[/color]},
				[color=#19177C]$opts[/color]{[color=#BA2121]'command'[/color]},
				[color=#19177C]$opts[/color]{[color=#BA2121]'path'[/color]},
				[color=#19177C]$opts[/color]{[color=#BA2121]'configFile'[/color]},
				[color=#19177C]$opts[/color]{[color=#BA2121]'i'[/color]}
			);
			[color=#008000]**my**[/color] [color=#19177C]$cmd[/color] [color=#666666]=[/color] [color=#BA2121]"$commandPath/$command $path/$configFile"[/color];
			[color=#008000]open[/color] ([color=#008000]**my**[/color] [color=#19177C]$logoutput[/color], [color=#BA2121]'>'[/color], [color=#BA2121]"$path/$output.$i"[/color]) [color=#666666]||[/color] [color=#008000]die[/color] [color=#19177C]$![/color];
			[color=#008000]open[/color] ([color=#008000]**my**[/color] [color=#19177C]$piperead[/color], [color=#BA2121]'-|'[/color], [color=#19177C]$cmd[/color]) [color=#666666]||[/color] [color=#008000]die[/color] [color=#19177C]$![/color];
			[color=#008000]**while**[/color] ([color=#666666]<[/color][color=#19177C]$piperead[/color][color=#666666]>[/color]) {
				[color=#008000]**print**[/color] [color=#19177C]$logoutput[/color] [color=#19177C]$_[/color];
			}
			[color=#008000]close[/color] [color=#19177C]$cmd[/color];
			[color=#008000]close[/color] [color=#19177C]$logoutput[/color];
	}));
}


[color=#408080]*#-----some code-----#*[/color]

run_parallel(
	[color=#BA2121]'commandPath'[/color] [color=#666666]=>[/color] [color=#19177C]$commandPath[/color], 
	[color=#BA2121]'command'[/color] [color=#666666]=>[/color] [color=#19177C]$command[/color], 
	[color=#BA2121]'path'[/color] [color=#666666]=>[/color] [color=#19177C]$path[/color], 
	[color=#BA2121]'configFile'[/color] [color=#666666]=>[/color] [color=#19177C]$configFile[/color], 
	[color=#BA2121]'i'[/color] [color=#666666]=>[/color] [color=#19177C]$i[/color]
);

[color=#408080]*#-----some code-----#*[/color]

[color=#408080]*#at end of program make sure you wait for all threads to finish*[/color]

[color=#008000]**foreach**[/color] ([color=#19177C]@THREADS[/color]) {
	[color=#19177C]$_[/color] [color=#666666]->[/color] [color=#008000]join[/color]();
}

```

See perl's inbuilt [threads]("http://perldoc.perl.org/threads.html") pragma.

---

### Post by ibuclaw on 2010-06-11
> **steve_c said:**
> I have a program where I'm using Parallel::ForkManager to help parallelize a section of code. It has a main process and no more than 8 child processes at a time (if I'm using ForkManager right). During the child processes it calls an external program that takes some time to execute and a fair amount of memory (hence why I'm trying to limit the number of simultaneous processes).

At first during the child threads, in my naivety I was using exec() to call the external program. That obviously created another, unattached child process, which then allowed its parent to finish quickly, then opening up one of the 8 slots for the next job, and so on, without giving the external program time to finish. This quickly ate all my RAM and locked up the machine.

So now I'm using system() to call the external program, and it *seems* to be working, but with a catch. I need to redirect the output from the external program to a log file. For some reason this worked fine with exec() but is not working with system(). I know that the other output files are being created, but not the redirected output. So it seems that I'm just not understanding something about how to properly use perl's system() command. Any thoughts?

Here is the external command:
```
system "$commandPath/$command $path/$configFile > $path/output.$i &";
```

Thanks for any help.

Why not use open() ?

```

open my $command, "$commandPath/$command $path/$configFile |"
open my $output, "> $path/output.$i"
while (<$command>)
{
    print $output $_;
}
close $command;
close $output;

```

Regards.


Edit: pfft. dv beat me. :)

---

### Post by steve_c on 2010-06-11
Turns out my problem was actually with the name of the output file. I generalized it which was stupid on my part, but the name was actual line in the code was:
```
system "$commandPath/$command $path/$configFile > $path/$seed_run1.out$i &"
```
The & was a problem. But even after removing that it still wouldn't create the output file, which I think may be related to the underscore. Once I changed it to $seed.$i.out that seems to work much better.

Thank you very much dv3500ea and ibuclaw! I'm not very experienced/good with perl yet so if using system seemed weird, that's only because I'm coming from more of a php background.

dv3500ea, I feel like your threads and pipes suggestion is probably technically a better solution (I could be mistaken though), and I may try to rewrite this program to use perl's threading some other time. Right now though it was very important to make sure that no more than X processes were running at any one time (in this case 7, because the machine has 8 processor cores and we wanted to leave one open for system activity) and the entire job covers 1000 runs. The ForkManager package I found limits the number of processes running at any one time, so that was a real benefit to me. Had I tried to go from your code I would've had to reimplement some sort of thread capping. I really appreciate the example though and I'm probably going to use it as a starting point to learn more about threading with perl.

ibuclaw, I wound up switching to using open() like you and dv suggested. I just wasn't aware that open() on perl could be used like that. As I mentioned before, php is most of my scripting language background, and there I use fopen() to open files (which I equated to open() in perl) and system()/exec() to make system calls. Thank you both for educating me on that one.

Again, thank you.

---

### Post by dv3500ea on 2010-06-11
To be honest, I didn't know much of that off by heart (like I can never remember which way round pipes go for input/output; '-|' or '|-'). I used [this website: http://perldoc.perl.org/index.html]("http://perldoc.perl.org/index.html") which is a wonderful resource for learning/referencing anything to do with perl and its core libraries.

---

### Post by ibuclaw on 2010-06-11
> **dv3500ea said:**
> To be honest, I didn't know much of that off by heart (like I can never remember which way round pipes go for input/output; '-|' or '|-'). I used [this website: http://perldoc.perl.org/index.html]("http://perldoc.perl.org/index.html") which is a wonderful resource for learning/referencing anything to do with perl and its core libraries.

I know the feeling.

I still get muddled in the difference between $+ and $- sometimes. ;)

---

