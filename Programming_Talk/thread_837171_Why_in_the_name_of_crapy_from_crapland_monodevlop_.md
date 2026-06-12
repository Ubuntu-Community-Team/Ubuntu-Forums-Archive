---
title: "Why in the name of crapy from crapland monodevlop doesnt show the blackbox it should"
date: 2008-06-22
forum: Programming Talk
---

### Post by dinbrca on 2008-06-22
i am new to monodevlop and i didnt get it:
why cant i see the blackbox (the cmd in windows) when i create a console application in c#. this is my code:
```

			Console.WriteLine("Enter User");
			string user;
			user=Console.ReadLine();
			Console.Clear();
			Console.WriteLine("Hello " + user + "!");
			int s;
			s=int.Parse(Console.ReadLine());
			if (s==0)
			{
				Console.WriteLine("Correct");
			}
			else
			{
				Console.WriteLine("Incorrect");
			}

```

---

### Post by fahadsadah on 2008-06-22
You need to execute the program in a Terminal outside of MonoDevelop.
Double clicking doesn't work either.

---

### Post by true_friend on 2008-06-22
The project type should be Console Application (similiar to sharp develop and visual studio) and the output of the console will be displayed under the editor area. You can see the screen shot where the out put of the console is displayed after the project is built.
[IMG]http://img385.imageshack.us/img385/7320/snapshot1ht2.png[/IMG]
Regards

---

### Post by dinbrca on 2008-06-22
yes but if there is a console.readline() i cant enter something..

---

### Post by dinbrca on 2008-06-23
someone?

---

### Post by henchman on 2008-06-23
> **dinbrca said:**
> someone?

> **fahadsadah said:**
> You need to execute the program in a Terminal outside of MonoDevelop.
Double clicking doesn't work either.

This doesn't work for you?

```
mono program.exe
```

---

### Post by Zugzwang on 2008-06-23
> **dinbrca said:**
> yes but if there is a console.readline() i cant enter something..

That might simply be unsupported by MonoDevelop. You might have to run it in the terminal.

---

### Post by true_friend on 2008-06-28
Yeah it looks it is. There is no way to give input. It only works in terminal.

---

### Post by true_friend on 2008-06-28
There is an external conole available. It is not activated by default. Go to Project>Options>Configurations (node) > Output (sub-node) and enable extrnal console.
Regards

---

### Post by Sukarn on 2008-06-28
> **true_friend said:**
> There is an external conole available. It is not activated by default. Go to Project>Options>Configurations (node) > Output (sub-node) and enable extrnal console.
Regards

That sadly means that it has to be enabled on a per-project basis, and cannot be enabled for something like single-file.cs because that does not fall under a project and the button remains greyed out.

I've recently been using Gedit with the plugin "Embedded Terminal" to write, compile and run C# as I'm learning it.

---

### Post by true_friend on 2008-06-29
thats a good idea. I use kate sometime for same purpose. The problem is this you have to reset it on every restart. Not on every new project. It is program setting but it does not save. There is something wrong with it.
Regards

---

### Post by Sukarn on 2008-06-30
> **true_friend said:**
> The problem is this you have to reset it on every restart. Not on every new project. It is program setting but it does not save. There is something wrong with it.
Regards

Oh, I tried that setting with two different projects, and I had to enable it on each of them separately, so I thought that its a per-project setting. I did not pay heed to the fact that I had closed monodevelop in between.

---

### Post by true_friend on 2008-06-30
I was wrong buddy. It is project option. But it is a bug not saving this setting. People at monodevelop list asked me to file a bug so I filed a bug. Now see and wait when it is fixed. 
Regards

---

