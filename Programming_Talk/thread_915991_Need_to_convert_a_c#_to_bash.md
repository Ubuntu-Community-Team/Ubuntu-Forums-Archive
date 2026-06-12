---
title: "Need to convert a c# to bash"
date: 2008-09-10
forum: Programming Talk
---

### Post by lsutiger on 2008-09-10
I am attaching to small c# scripts that I used in windows in order to zip a bunch of files for archive and rename them to a standard.

I would like to use bash in order to make this happen, but not sure where to really start.
I have Apress' From Bash to Z Shell and Oreilly's Learning the Bash Shell for reference, but I yet to get through the whole books.

Could someone nudge me in the right direction?
Thanx

---

### Post by cb951303 on 2008-09-10
you know you can use C# in linux right? Anyway if your aim is 'learning the bash" then this howto will get you started pretty fast [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by lsutiger on 2008-09-10
Thanx for the reply. I tried using mono-develop with c# but couldn't find much on documentation on their website.

Will do!

---

### Post by Tomosaur on 2008-09-10
> **lsutiger said:**
> Thanx for the reply. I tried using mono-develop with c# but couldn't find much on documentation on their website.

Will do!

Mono is basically an implementation of .Net. If you're ok with C#, and you used the .Net framework to create your programs, then provided you didn't use anything 'too' bleeding edge with .Net, you should be ok. The Mono .Net is, for obvious reasons, incomplete, but for most common things you should have no problem porting your programs.

The Mono Class Library: [http://www.go-mono.com/docs/index.aspx?tlink=root:/classlib](http://www.go-mono.com/docs/index.aspx?tlink=root:/classlib)

---

### Post by qstraza on 2008-09-10
> **lsutiger said:**
> I am attaching to small c# scripts that I used in windows in order to zip a bunch of files for archive and rename them to a standard.

I would like to use bash in order to make this happen, but not sure where to really start.
I have Apress' From Bash to Z Shell and Oreilly's Learning the Bash Shell for reference, but I yet to get through the whole books.

Could someone nudge me in the right direction?
Thanx
I can try to write a script for you if you tell me exectly what you want. I like bashing around:p Im not an expert though, but learning while solving new problems;)

---

### Post by lsutiger on 2008-09-10
Thanx to both.

I am little lost in Mono, because of stuff like this.
[http://www.go-mono.com/docs/index.aspx?tlink=root:/classlib](http://www.go-mono.com/docs/index.aspx?tlink=root:/classlib)

As you can see, the Process Class is under System.Diagnostic. I have using System.Diagnostic at the beginning of the program. But when I try to use it I get 
The type or namespace name `Process' could not be found. Are you missing a using directive or an assembly reference?

From this code:
Process myProcess = new Process();

sorta dumbfounded...

---

### Post by lsutiger on 2008-09-10
OK Restarted the whole project and it worked. I am going to try this in C# on linux. 
However I am pulling my hair out about how to run through the program in debug mode. The equivalent in MS-VS would be to mark a bookmark in the code and click on Debug-->Start or press F5. Press F5 in Mono just runs the project.

---

### Post by lsutiger on 2008-09-10
UPDATE: I am still looking for debug mode, but I have a problem I just can not understand.
Here is the code```
strArgs = DateTime.Now.AddMonths(-1).ToShortDateString();

				strArgs = strArgs.PadLeft(10,'0');

				strArgs = strArgs.Remove(2,4);

				file = file.PadLeft(2,'0');
				strArgs = " /home/brian/EOM" + file + strArgs + ".ZIP";

				path = " /home/brian/EOM/" + file + "/*.M*";

				strArgs = strArgs + path;
				Console.Write(strArgs);

				myProcess.StartInfo.FileName = "zip -r ";

				myProcess.StartInfo.Arguments = strArgs;

				myProcess.StartInfo.CreateNoWindow = true;
try

				{

					myProcess.Start();

					myProcess.WaitForExit();

				

				}

				catch (SystemException caught)

				{

					Console.WriteLine(caught.ToString());

					continue;

				}
```
Which executes the following:```
zip -r  /home/brian/EOM02082008.ZIP /home/brian/EOM/02/*.M*
```

but I am getting this from running it:```
 /home/brian/EOM01082008.ZIP /home/brian/EOM/01/*.M*	zip warning: name not matched: /home/brian/EOM/01/*.M*
```

Yet when I do this from the CLI ```
zip -r /home/brian/EOM01082008.zip /home/brian/EOM/01/*.m*
```

It works.....Anybody see anything wrong here?

---

### Post by cb951303 on 2008-09-10
AFAIK monodevelop has not debug support yet

just echo strArgs and path to console to see if there is some false char or something

---

### Post by lsutiger on 2008-09-10
Ah yes..that was included in the previous post. I wrote Console.Write(strArgs);
under strArgs = strArgs + path;
The output is /home/brian/EOM01082008.ZIP /home/brian/EOM/01/*.M*

I truly appreciate your help.

---

### Post by lsutiger on 2008-09-10
I ended up trying tar and it worked just as planned.
Odd that zip would not recognize the arguments, even though those files were there..I was trying to use wildcards...maybe that was the problem?
It just doesn't make sense to me.
But thanx for your input! Now that I can write programs in c# for linux, I am one more step away from getting rid of Windows for good.

---

### Post by true_friend on 2008-09-11
[Official forums]("http://www.go-mono.com/forums/") help me lot when I have a question about mono.

---

### Post by lsutiger on 2008-09-11
Thanx a bunch!
I ended up getting the zip to work. I needed that mainly for windows compatibility.
It seems the switchs/option are a bit different from winzip command line.

---

### Post by lsutiger on 2008-09-27
OK...so over the last two weeks I have gotten familiar with mono and converted all of my daily report programs to run on Ubuntu. Awesome!

But when it comes to the GTK visual designer I am very lost. As far as google, I got a few relevant posts, but nothing comprehensive. 

I am formerly familiar with C++, and used to program for Windows 95/98, before there were visual designers and had to code all those windows by hand. If I need to go back to that and relearn C++ thats fine, plus a challenge. But what book or tutorial out there is the absolute best for learning C++ GTK Programming? I have been stiffed by a few books I have bought in the past, and stopped buying. I have one from Orielly on Bash that was very helpful, but I don't use Bash everyday, so it's mostly a desk reference.

Thanx for any info!

---

### Post by true_friend on 2008-09-27
Gtk is written in C not c++, there are bindings available for c++, c#, python etc. You can use [gtk+ development]("http://www.gtkbook.com/home.php") which will enable you to learn basics of gtk+ and then you can use same code in every language that has gtk bindings with little change in syntax. 
Regards

---

