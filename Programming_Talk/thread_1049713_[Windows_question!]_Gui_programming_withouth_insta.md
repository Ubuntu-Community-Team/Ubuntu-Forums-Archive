---
title: "[Windows question!] Gui programming withouth installing something"
date: 2009-01-24
forum: Programming Talk
---

### Post by orlox on 2009-01-24
Hi! I suddenly find myself needing to program an stupidly simple windows application, that opens a file dialog to open a file, reads the file, and creates a new file based on the original one with slight modifications...

The thing is...I make an executable that works without needing to install anything else...Soooo, the question iiiiis...What is the easy way to get a file dialog (the programming language doesnt matter, but it has to be a compiled program) without having to install anything on a fresh windows xp install???

---

### Post by slavik on 2009-01-24
Vb6?

---

### Post by DocForbin on 2009-01-24
check out autohotkey. it can make standalone executables and basic gui stuff is super easy.

---

### Post by orlox on 2009-01-24
```
Vb6?
```
Wouldnt the client machine require to install dotnet???
```
check out autohotkey
```
I dont now if that would fit my needs...I need to open the file and do many string operations on it and the scripting language autohotkeys uses doesnt seem worth to learn only for this...

---

### Post by DocForbin on 2009-01-24
> ```
check out autohotkey
```
I dont now if that would fit my needs...I need to open the file and do many string operations on it and the scripting language autohotkeys uses doesnt seem worth to learn only for this...
well, c/c++, python executable (dunno what options there are today for this, but you could do it years ago), java (if the runtime being installed is okay, if not you can use exe4j)

---

### Post by Kilon on 2009-01-24
> **orlox said:**
> Hi! I suddenly find myself needing to program an stupidly simple windows application, that opens a file dialog to open a file, reads the file, and creates a new file based on the original one with slight modifications...

The thing is...I make an executable that works without needing to install anything else...Soooo, the question iiiiis...What is the easy way to get a file dialog (the programming language doesnt matter, but it has to be a compiled program) without having to install anything on a fresh windows xp install???

In MACOS and linux , Java comes preinstalled. In windows it does not.

making your program in java is a valid solution.

---

### Post by orlox on 2009-01-24
I really like java, and would prefer that as an alternative, but the client for wich I need to do this doesnt want the application to have any installation prerequisites...I dont know if executables created from java work without an installed JRE...

---

### Post by wmcbrine on 2009-01-24
I hate to say it, but VBScript may actually be the appropriate solution in this case.

---

### Post by DocForbin on 2009-01-24
> **orlox said:**
> I really like java, and would prefer that as an alternative, but the client for wich I need to do this doesnt want the application to have any installation prerequisites...I dont know if executables created from java work without an installed JRE...
they don't, but you can use programs like exe4j to make a standalone exe

---

### Post by slavik on 2009-01-24
> **orlox said:**
> ```
Vb6?
```
Wouldnt the client machine require to install dotnet???
```
check out autohotkey
```
I dont now if that would fit my needs...I need to open the file and do many string operations on it and the scripting language autohotkeys uses doesnt seem worth to learn only for this...
check again :) ... there is vb6 and then there is vb.net

---

### Post by Frak on 2009-01-24
Use vb6. It's different than vb.net IIRC.

EDIT
Never mind, I didn't read the rest again.

---

### Post by slavik on 2009-01-24
does that just embed a JRE along with a JAR?

---

### Post by Frak on 2009-01-24
> **slavik said:**
> does that just embed a JRE along with a JAR?
j2exe, yes. It also installs one with the program IIRC.

---

### Post by orlox on 2009-01-24
exe4j needs a license for non-evaluation purposes so its not a viable alternative

---

### Post by orlox on 2009-01-24
Just found a solution with c++:
```

#include <windows.h>
#include <string.h>
#include <stdio.h>

int main(void)
{
	OPENFILENAME file; BOOL bret; char FileName[1000]="";       
	memset(&file,0,sizeof(file));   
	file.lStructSize = sizeof(file);
	file.Flags = OFN_HIDEREADONLY;
	file.lpstrFile=FileName; file.nMaxFile=1000;
	file.lpstrFilter="Archivo CSV(*.csv)\0*.csv\0";
	do{
		bret=GetOpenFileName(&file);
		if(bret==FALSE)
		{
			MessageBox(NULL, "Debe seleccionar un archivo", "ERROR", MB_OK);
		}else{
			MessageBox(NULL, FileName, "OK", MB_OK);
		}
	}while(bret==FALSE);
	return 0;
}

```
That works like a charm! and I can create the executable on linux using mingw!

---

### Post by Kilon on 2009-01-25
> **orlox said:**
> I really like java, and would prefer that as an alternative, but the client for wich I need to do this doesnt want the application to have any installation prerequisites...I dont know if executables created from java work without an installed JRE...


But I have already told you ! Java is already installed in Linux, there is no installation prerequisites ! No a jar wont work without a JRE. 

However you have to remember that preinstallation should not be an issue. 

For example I was first introduced to python by a game called "Freedom Force" which was using python as its script engine. At the time there was no python installation in my computer and I had never heard of python. The game never actually required to have a python installation or an internet connection in order to download it by itself. 

Nope

Python was bundled in, with the installation of Game. Once I installed the game , python was installed as well.  

You can do the same with any programming language, there many excellent programs out there that make bundle installations. I agree that requiring the user to install these packages by himself could be  a source of big frustration for the user. But your "problem" is not really a problem.

---

### Post by nvteighen on 2009-01-25
> **orlox said:**
> I really like java, and would prefer that as an alternative, but the client for wich I need to do this doesnt want the application to have any installation prerequisites...I dont know if executables created from java work without an installed JRE...

Well, actually, a program that is absolutely standalone would be a bootloader... :)

---

### Post by orlox on 2009-01-25
```

But I have already told you ! Java is already installed in Linux, there is no installation prerequisites ! No a jar wont work without a JRE.

```

The client is a windows machine that because of the clients decision, must not have anything but windows installed to work. In any case I already solved it with c++, but this part of the forums doesnt seem to allow me to mark my thread solved

---

### Post by NathanB on 2009-01-25
I've always used AutoIt for these "one off" simple proggies.

[http://www.autoitscript.com/autoit3/index.shtml](http://www.autoitscript.com/autoit3/index.shtml)

Pros:
 1) lightweight (compared to VB6)
 2) no dependencies
 3) less complicated than VB or VBscript

However, I like your demonstration of how easy it can be accomplished with C++ code.

---

### Post by The Cog on 2009-01-25
python has a py2exe utility that bundles the python interpreter and the needed library files into a standalone exe file. I gather it's smart enough to only include the libraries you use in the program to avoid bloat.

---

### Post by brentoboy on 2009-01-26
You should seriously consider vbscript.

Java requires the runtime.
VB6 requires its own runtime (3 MB of DLLs)
C/C++ will get really hairy if they decide to add any features down the road - direct windows API programming takes time.

VBScript is already installed as part of windows, and it works like a charm.

```

Set CommonDlg = CreateObject("UserAccounts.CommonDialog") 
If CommonDlg.ShowOpen() Then  'returns false if they cancel
	MsgBox CommonDlg.FileName
End If

```

It might be a "silly" language, but vbscript has its uses.

---

