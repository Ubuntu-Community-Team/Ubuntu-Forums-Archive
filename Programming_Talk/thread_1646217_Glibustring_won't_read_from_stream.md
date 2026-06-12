---
title: "Glib::ustring won't read from stream?"
date: 2010-12-15
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-15
Glib::ustream is normally a plug-and-play replacement for std::string except it handles international character sets... but inexplicably it won't work with stream input, e.g. :
```

$> ./charcode
enter text to see unicode values
abc
ULine=abc, size=3, codes: 000061 000062 000063
&#8364;
Glib::ConvertError, Code=ILLEGAL_SEQUENCE

```

that is the output from following program:
[php]
// g++ -o charcode charcode.cpp `pkg-config --cflags --libs gtkmm-2.4`
#include <iostream>
#include <string>
#include <cstdio>
#include <glibmm/ustring.h>
#include <glibmm/convert.h>

using namespace std;

int main(int argc, char *argv[], char *envp[]) {
	printf("enter text to see unicode values\n");
	try {
		while (cin.good()) {
			Glib::ustring aULine;
// reading to std:string and then copying it to ustring works ?!
#ifdef FIXME
			string aLine;
			cin >> aLine;
			aULine = aLine;
#else
			cin >> aULine;
#endif
			printf("ULine=%s, size=%u, codes:",
				aULine.c_str(), (unsigned) aULine.size()
			);
			for (int i = 0; i < aULine.size(); ++i) {
				printf(" %06X", (gunichar) aULine[i]);
			} printf("\n");
		}
	} catch (Glib::ConvertError iE) {
		const char * aCodeName[] = {
			"NO_CONVERSION", "ILLEGAL_SEQUENCE", "FAILED",
			"PARTIAL_INPUT", "BAD_URI", "NOT_ABSOLUTE_PATH"
		};
		return !!printf("Glib::ConvertError, Code=%s\n", aCodeName[iE.code()]);
	}
	return !printf("Exits Normally\n");
}
[/php]
however if I recompile to use an intermediary std::string it works :confused:
```

$> g++ -DFIXME -o charcode charcode.cpp `pkg-config --cflags --libs gtkmm-2.4`
$> ./charcode
enter text to see unicode values
abc
ULine=abc, size=3, codes: 000061 000062 000063
&#8364;
ULine=&#8364;, size=1, codes: 0020AC

```
... see now the Euro character &#8364; (Alt E on my keyboard) is read just fine :shock: I don't understand why Glib::ustring can't read it :(

---

