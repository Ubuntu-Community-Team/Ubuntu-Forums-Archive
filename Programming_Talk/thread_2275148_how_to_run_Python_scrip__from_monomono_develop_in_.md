---
title: "how to run Python scrip  from mono/mono develop in ubuntu"
date: 2015-04-24
forum: Programming Talk
---

### Post by rahil2 on 2015-04-24
[FONT=Helvetica Neue]I want to run the following python script using C# and MonoDevelop and execute the code. My Mono Develop code[/FONT]
[COLOR=#00008B]string[/COLOR][COLOR=#000000] command [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]"python"[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]string[/COLOR][COLOR=#000000] argss [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]"/home/xyz/script.py A_file B_file"[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]string[/COLOR][COLOR=#000000] verb [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]""[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#2B91AF]ProcessStartInfo[/COLOR][COLOR=#000000] procInfo [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#00008B]new[/COLOR][COLOR=#2B91AF]ProcessStartInfo[/COLOR][COLOR=#000000]();[/COLOR][COLOR=#000000]
        procInfo[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]WindowStyle[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#2B91AF]ProcessWindowStyle[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]Normal[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]
        procInfo[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]UseShellExecute[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#00008B]false[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]
        procInfo[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]FileName[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] command[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]  
        procInfo[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]Arguments[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] argss[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]    
        procInfo[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]Verb[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] verb[/COLOR][COLOR=#000000];[/COLOR][COLOR=#000000]         
        [/COLOR][COLOR=#2B91AF]Process[/COLOR][COLOR=#000000].[/COLOR][COLOR=#2B91AF]Start[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]procInfo[/COLOR][COLOR=#000000]);[/COLOR][FONT=Helvetica Neue]The above code is not working. It is showing A_file & B_File are not accessible. even A_File & B_File has been give full permission & file is placed at same location. python script is working correctly when compile directly on terminal. I am running MonoDevelop on Ubuntu[/FONT]

---

### Post by ian-weisser on 2015-04-24
'Not accessible' seems like* **the application you are running*** needs permission to run A_file and B_file.

---

### Post by rahil2 on 2015-04-24
both the file have full permission, they are working fine when running directly on terminal
it showing error: 
sh 0: can't open A_file.sh

---

### Post by ofnuts on 2015-04-24
Are "A_file" and "B_file" absolute or relative paths, and in the latter case have you checked that the current directory is actually what you assume it is?

---

