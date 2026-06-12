---
title: "Eclipse CDT Error"
date: 2006-04-07
forum: Programming Talk
---

### Post by HokeyFry on 2006-04-07
I just installed Eclipse and installed the CDT plugin for it. I made a sample program to test if it runs:

```

#include <iostream>

using namespace std;

int main() {
	cout << "Test..." << endl;
	return 0;
}

```

I get two errors in the error bar at the bottom:

***No rule to make target 'all'.
***No rule to make target 'clean'.

Anyone know the problem? And to think I was so hyped about finally getting a C++ IDE to work in linux...

---

### Post by tageiru on 2006-04-09
Thats actually errors produces by the make build system, which, if a remember correctly, is used as the build system for CDT.

Perhaps you need to instruct Eclipse to create a Makefile for you, or do it manually.

---

### Post by Corvillus on 2006-04-16
I don't think Eclipse's automatic building features work with CDT. Mine works fine only after turning off Project -> Build automatically. After doing that, then going to project -> build all for each recompile, it worked fine.

---

### Post by unbuntu on 2006-04-16
[QUOTE=Corvillus]I don't think Eclipse's automatic building features work with CDT. Mine works fine only after turning off Project -> Build automatically. After doing that, then going to project -> build all for each recompile, it worked fine.[/QUOTE]
It actually does.  (at least for my C projects)

[QUOTE=HokeyFry]I just installed Eclipse and installed the CDT plugin for it. I made a sample program to test if it runs:

```

#include <iostream>

using namespace std;

int main() {
	cout << "Test..." << endl;
	return 0;
}

```

I get two errors in the error bar at the bottom:

***No rule to make target 'all'.
***No rule to make target 'clean'.

Anyone know the problem? And to think I was so hyped about finally getting a C++ IDE to work in linux...[/QUOTE]
I think what you need is to hand-code a Makefile, and add the targets to Eclipse's build target using the menu.  At least that's how I did, and it's not a CDT error.

---

