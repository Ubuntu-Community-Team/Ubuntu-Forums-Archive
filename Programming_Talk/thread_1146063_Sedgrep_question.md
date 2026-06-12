---
title: "Sed/grep question"
date: 2009-05-02
forum: Programming Talk
---

### Post by WitchCraft on 2009-05-02
The following situation:
A class implementation in Cquake.cpp

Now I want to automatically generate the header file (so I don't always have to add them manually when I extend Cquake.cpp)

Now I use the following command line to get the function definitions:
```

 grep "Cquake" ./Cquake.cpp | sed 's/Cquake\:\://g;s/$/\;/g;/#include/d'

```
which is equivalent to
```

sed '/Cquake\:\:/!d;s/Cquake\:\://g;s/$/\;/g;/#include/d' ./Cquake.cpp

```

or to
```

awk '{if($0 ~ "Cquake::") {sub(/Cquake::/,"");print $0} else {}}' ./Cquake.cpp

```


which outputs me a list of all function definitions in Cquake.cpp
e.g.
```

void CG_Init(int serverMessageNum, int serverCommandSequence, int clientNum);
void QDECL CG_Printf(const char *msg, ...);
void QDECL CG_Error(const char *msg, ...);
void QDECL Com_Printf(const char *msg, ...);
void QDECL Com_Error(int level, const char *error, ...);
const char* CG_ConfigString(int index);
void CG_SetConfigValues(void);
void CG_ParseServerinfo(void);
void CG_ExecuteNewServerCommands(int latestSequence);
void CG_ServerCommand(void);
void CG_NewClientInfo(int clientNum);
void CG_RegisterClients(void);

```

The problem is,  I made newlines when my function definitions takes too many arguments.
```

void Cquake::CG_DrawStringExt( int x, int y, const char *string, const float *setColor,
		qboolean forceColor, qboolean shadow, int charWidth, int charHeight, int maxChars )

```

And when my grep/sed code goes over it, i get:
```

void CG_DrawStringExt( int x, int y, const char *string, const float *setColor,;

```

instead of
```

void CG_DrawStringExt( int x, int y, const char *string, const float *setColor,
		qboolean forceColor, qboolean shadow, int charWidth, int charHeight, int maxChars );

```

I need to know how I can get the entire line until the { sign ?

---

### Post by akudewan on 2009-05-02
> **WitchCraft said:**
> The following situation:
I need to know how I can get the entire line until the { sign ?

If I understand correctly, you need to select lines between *CQuake::* and *{*

You could do that using:
```

sed -n '/CQuake::/,/{/p' ./CQuake.cpp

```

You could use this instead of the grep command and make necessary changes to the piped sed command.

Hope this helps.

---

### Post by Arndt on 2009-05-02
> **akudewan said:**
> If I understand correctly, you need to select lines between *CQuake::* and *{*

You could do that using:
```

sed -n '/CQuake::/,/{/p' ./CQuake.cpp

```

You could use this instead of the grep command and make necessary changes to the piped sed command.

Hope this helps.

I came up with this, in one single 'sed' command:

```
sed -n '/CQuake::/,/^{/{s/CQuake:://g;s/)$/);/;/^{/d;p}' CQuake.cpp
```

It assumes that the { starts a line. It also assumes that the ) of the parameter list is last on its line (no extra whitespace or comment there).

---

### Post by WitchCraft on 2009-05-02
Solved, the solution is:
```

cat Cquake.cpp | sed 's/^\s*//g;s/\s*$//g' | sed -e :a -e '/abba$/N; s/abba\n//; ta'| sed '/Cquake\:\:/!d;s/Cquake\:\://g;s/$/\;/g;/#include/d'

```
 
where abba is the pattern to match at the end of the line
 
and on MinGW under windows it's different:
```

sed 's/^ *//g;s/ *$//g' Cquake.cpp | sed -e :a -e '/,$/N; s/,\n/,/; ta' | sed '/Cquake\:\:/!d;s/Cquake\:\://g;s/$/;/g' | uniq

```

---

### Post by WitchCraft on 2009-05-02
> **Arndt said:**
> I came up with this, in one single 'sed' command:

```
sed -n '/CQuake::/,/^{/{s/CQuake:://g;s/)$/);/;/^{/d;p}' CQuake.cpp
```

It assumes that the { starts a line. It also assumes that the ) of the parameter list is last on its line (no extra whitespace or comment there).


Correct, that's a more elegant solution than mine.
However, I take whitespaces into account. You can trim them away:
```

sed 's/^\s*//g;s/\s*$//g' 

```

---

### Post by WitchCraft on 2009-05-02
> **Arndt said:**
> I came up with this, in one single 'sed' command:

```
sed -n '/CQuake::/,/^{/{s/CQuake:://g;s/)$/);/;/^{/d;p}' CQuake.cpp
```

It assumes that the { starts a line. It also assumes that the ) of the parameter list is last on its line (no extra whitespace or comment there).

Finally, here, trimming whitespaces:
```

sed -n 's/^\s*//g;s/\s*$//g;/Cquake::/,/^{/{s/Cquake:://g;s/)$/);/;/^{/d;p}' Cquake.cpp

```

Thanks Arndt!

---

### Post by WitchCraft on 2009-05-02
Now I have a problem with the $ sign in the makefile...
You need to double the $ sign

---

### Post by WitchCraft on 2009-05-02
Now I have a problem with the makefile:

```

$(STORE)/%.o: %.cpp
	@echo Creating object file for $*...
	sed -n 's/^\s*//g;s/\s*$$//g;/Cquake::/,/^{/{s/Cquake:://g;s/)$$/);/;/^{/d;p}' $*.cpp > $*.dec
	@$(CC) -Wp,-MMD,$(STORE)/$*.dd $(CCPARAM) $(foreach INC,$(INCPATH),-I$(INC))\
                $(foreach MACRO,$(MACROS),-D$(MACRO)) -c $< -o $@
	@sed -e '1s/^\(.*\)$$/$(subst /,\/,$(dir $@))\1/' $(STORE)/$*.dd > $(STORE)/$*.d
	@rm -f $(STORE)/$*.dd

```

where $* is ./Cquake.cpp and ./Cos.cpp and ./Ccrc32.cpp and ./Cthreading.cpp etc.

i need to substitute the Cquake in the sed directive
```

sed -n 's/^\s*//g;s/\s*$$//g;/Cquake::/,/^{/{s/Cquake:://g;s/)$

``` 

with the result of 
```

echo "$*" | sed 's/\.\///'

```

which is Cquake and Cos and Ccrc32

---

### Post by WitchCraft on 2009-05-02
Solved the problem.
Of course, you can access an environment variable from sed with the syntax:
```

export MYVAR="Any"
echo "SomeText" | sed 's/Some/'$MYVAR'/'

```

But the problem was, that the parent process is 'make', which is processing the Makefile. 

When it reaches the "export CLASSNAME=Cquake" line, it will create a child process which runs a shell to execute the export statement. The problem is of course that the variable is set in the environment of the child process only. After the export statement is completed, the child process exits and its environment, including the new variable, is gone. The "echo $CLASSNAME" statement is executed by another child process...


The problem's solution is to join the variable initialization and the variable use into a single shell command, so that one child shell will execute both:

```

all: RELEASE

RELEASE:
        export CLASSNAME="Cquake"; \
        echo $$CLASSNAME

```

Not very flexible, but it works...

```

$(STORE)/%.o: %.cpp
	@export CLASSNAME="$$(echo "$*" | sed 's/\.\///')"; echo "Creating member function class declaration for class $$CLASSNAME...";\
	sed -n 's/^\s*//g;s/\s*$$//g;/'$$CLASSNAME'::/,/^{/{s/'$$CLASSNAME':://g;s/)$$/);/;/^{/d;p}' $*.cpp | uniq > $*.dec;\
	echo Creating object file for class $$CLASSNAME...
	@$(CC) -Wp,-MMD,$(STORE)/$*.dd $(CCPARAM) $(foreach INC,$(INCPATH),-I$(INC))\
                $(foreach MACRO,$(MACROS),-D$(MACRO)) -c $< -o $@
	@sed -e '1s/^\(.*\)$$/$(subst /,\/,$(dir $@))\1/' $(STORE)/$*.dd > $(STORE)/$*.d
	@rm -f $(STORE)/$*.dd

```

---

