---
title: "C++ iostream path"
date: 2009-06-21
forum: Programming Talk
---

### Post by jfitzpat on 2009-06-21
Hi,

I am getting an error on the last line posted here. I have printed the string and it works as i want it too, but using it as the path for the iostream is not working.

```
	
//included stuff:
#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
.
.
.
.
.
string folder;
cout << "Enter folder name: ";
cin >> folder;
string path = "saves\\" + folder + "\\players.ehm";
ifstream PlayersFile;
PlayersFile.open(path);
```

Thanks for any help,
-Jason

---

### Post by MadCow108 on 2009-06-21
ifstream open only takes cstrings.
so add a .c_str()
PlayersFile.open(path.c_str());

---

