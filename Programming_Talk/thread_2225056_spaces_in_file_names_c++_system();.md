---
title: "spaces in file names c++ system();"
date: 2014-05-19
forum: Programming Talk
---

### Post by brick2 on 2014-05-19
I am aware that this question has been asked over and over again, but I  just can get it to work, I wonder who was the genius that came up with  the idea to have spaces in file names.

```
system("copy C:\\Users\\test\\Desktop\\myProgram.exe C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup"); 
```

This was the simplest was to make my program run on start up I know it  is not the most efficient one but than again I am not an expert.

If someone could please help me out with this, I value all suggestions.
I have attempted several combinations with double quote but failed.

---

### Post by brick2 on 2014-05-19
I am sure that the solution is pretty simple but I just need a fresh pair of eyes to have a look, just need to arrange quotes in a proper manner.

---

### Post by ofnuts on 2014-05-19
```

system("copy \"C:\\Users\\test\\Desktop\\myProgram.exe\" \"C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\"");

```

It is also possible that this makes it try to execute a "copy.exe" but there is no such beast Windows ("copy" is a built-in command). In which case you can try:
```

system("cmd /c copy ...");

```

Otherwise don't use system() but use one of the exec...() calls with xcopy.exe. Some of them let you specify individual arguments as strings. 

Now off to sanitize my keyboard after all that Windows stuff :)

---

### Post by brick2 on 2014-05-19
```
system("copy \"C:\\Users\\test\\Desktop\\myProgram.exe\" \"C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\"");
```

This did not do the trick. But thx for the effort, My connection sucks at the moment I ll try to see how xcopy() works.
I am running windows but only in a virtualbox, the host machine is fedora.

If anyone else has any other suggestions I am more than happy to take them.

---

### Post by brick2 on 2014-05-19
second option failed too 

system("cmd /c copy C:\\Users\\test\\Desktop\\recieveKey.exe C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup");

---

### Post by ofnuts on 2014-05-20
The solution with "cmd /c copy" also implies the double quotes around the file names.

---

### Post by brick2 on 2014-05-20
```
int main(int argc, char** argv)
{
    std::ifstream src(argv[0], std::ios::binary);
    std::ofstream dst("C:/ProgramData/Microsoft/Windows/Start Menu/Programs/Startup/myprogram.exe", std::ios::binary);
    dst << src.rdbuf();
    dst.close();
    src.close();
}
```

Solved the problem like this if anyone else encounters the same problem.
Thank you all for your time.

---

### Post by brick2 on 2014-05-20
But you need admin privileges due to the path.

---

### Post by ofnuts on 2014-05-20
Also you are resetting the change time on the executable, makes it hard to check later how up-to-date it is.

Btw, AFAIK, in "Startup" you shouldn't put programs but shortcuts to these... You are also likely reinventing the wheel, there are plenty of software installers around.

---

