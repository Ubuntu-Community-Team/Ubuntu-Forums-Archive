---
title: "A reference issue compiling in Eclipse"
date: 2013-01-20
forum: Programming Talk
---

### Post by indarkness on 2013-01-20
Hello,

I am compiling a C++ project with Eclipse on ubuntu 12.04 LTS, but I'm having a niggling issue with a library reference. The point is that I don't understand why this reference is causing trouble since it seems to be correct, I've attached a picture so as to show the dependency tree.

[IMG]http://i14.photobucket.com/albums/a331/ndarkness/Screenshotfrom2013-01-20195912_zps85325937.png[/IMG]

This is the TestUtils.cpp where the inclusion gives error
```
#include "TestUtils.h"

#include <ibrdtn/utils/Utils.h> //Sucks

CPPUNIT_TEST_SUITE_REGISTRATION (TestUtils);

void TestUtils::setUp()
{
}

void TestUtils::tearDown()
{
}

void TestUtils::tokenizeTest()
{
    using namespace dtn::utils;
    CPPUNIT_ASSERT(Utils::tokenize(":", "").empty());
    CPPUNIT_ASSERT(Utils::tokenize(":", "::").empty());
    CPPUNIT_ASSERT_EQUAL((int)Utils::tokenize(":", ":a:test::", 2).size(), 2);
    CPPUNIT_ASSERT_EQUAL((int)Utils::tokenize(":", ":a:test::b::", 2).size(), 3);
    //TODO how should the added string in the last item look like? "b::" or ":b::" or "::b::"
    CPPUNIT_ASSERT(Utils::tokenize(":", ":a:test::b::", 2)[2] == "b::");
    CPPUNIT_ASSERT_EQUAL((int)Utils::tokenize(":", ": :", 1).size(), 1);
    CPPUNIT_ASSERT_EQUAL((int)Utils::tokenize(":", ":    :t e s t: ").size(), 3);
}
```And the Utils.h which does not seem to exist is this
```

#ifndef UTILS_H_
#define UTILS_H_

#include "ibrdtn/data/Bundle.h"
#include <ibrcommon/data/BLOB.h>
#include <list>

namespace dtn
{
    namespace utils
    {
        class Utils
        {
        public:
            static void rtrim(std::string &str);
            static void ltrim(std::string &str);
            static void trim(std::string &str);

            static vector<string> tokenize(std::string token, std::string data, size_t max = std::string::npos);
            static double distance(double lat1, double lon1, double lat2, double lon2);

            static void encapsule(dtn::data::Bundle &capsule, const std::list<dtn::data::Bundle> &bundles);
            static void decapsule(const dtn::data::Bundle &capsule, std::list<dtn::data::Bundle> &bundles);

        private:
            static void encapsule(ibrcommon::BLOB::Reference &ref, const std::list<dtn::data::Bundle> &bundles);
            static double toRad(double value);
            static const double pi;
        };
    }
}

#endif /*UTILS_H_*/

```Any tip or advice?
Thanks in advance!!

---

### Post by ofnuts on 2013-01-21
Foreword: I have strictly no experience of CPP development under eclipse...

From the error message when TestUtils.cpp is compiled, the compiler is in some directory under "tests" (since it uses "../tests/Utils/TestUtils.cpp" to access the file), so it is looking for "ibrtn" under that directory, unless something tells it to also look under some other directory where it will find "ibrdtn". But this can't  be the "ibrdtn" project itself... I would try:
```

#include <utils/Utils.h>

```

---

### Post by indarkness on 2013-01-22
> **ofnuts said:**
> Foreword: I have strictly no experience of CPP development under eclipse...

From the error message when TestUtils.cpp is compiled, the compiler is in some directory under "tests" (since it uses "../tests/Utils/TestUtils.cpp" to access the file), so it is looking for "ibrtn" under that directory, unless something tells it to also look under some other directory where it will find "ibrdtn". But this can't  be the "ibrdtn" project itself... I would try:
```

#include <utils/Utils.h>

```

Thanks for the reply, I've tried it without success... I think it's some problem with eclipse include paths that I cannot figure out how to configure.:(

---

### Post by Warren Hill on 2013-01-22
Putting the header file in angle brackets

#include <utils/Utils.h>

tells the compiler that this is a standard header file so its probably looking in the wrong place

try 


#include "utils/Utils.h"

or 


#include "Utils.h"

May work better.  It will now look in the same directory as the other source files and should compile.

---

### Post by dwhitney67 on 2013-01-22
> **Warren Hill said:**
> Putting the header file in angle brackets

#include <utils/Utils.h>

tells the compiler that this is a standard header file so its probably looking in the wrong place

try 


#include "utils/Utils.h"

or 


#include "Utils.h"

May work better.  It will now look in the same directory as the other source files and should compile.
Or the OP could inform Eclipse as to where to find the header file(s).

Without the information on how Eclipse is building the project, I can only guess that a -I <path> statement is missing.

---

### Post by indarkness on 2013-01-22
Hi, thanks for your replies!!

I had already tried to use

```
#include "utils/Utils.h"

or 


#include "Utils.h"
```But without sucess, furthermore I had tried to change the include to use the commas instead of the  angle brackets getting the same error. 
Here the path settings of the project
[IMG]http://i14.photobucket.com/albums/a331/ndarkness/Screenshotfrom2013-01-22132052_zpsd7ee9b14.png[/IMG]


Now I'm almost sure that is a problem with the path since I have include some references in the project to the same project and some of the errors have disappeared( the Utils.h for instance) but new ones exact with the same sympthons have popped up in others files of the project as show this pic

[IMG]http://i14.photobucket.com/albums/a331/ndarkness/Screenshotfrom2013-01-22133229_zps60afd470.png[/IMG]

if you need more info please ask me!!

Thanks

---

### Post by dwhitney67 on 2013-01-22
> **indarkness said:**
> 
Now I'm almost sure that is a problem with the path...

Yes, it sure appears that way.  Have you considered clicking on the "Add" button to insert additional path(s) that lead to the header file(s) that Eclipse can't resolve?

> **indarkness said:**
> 
if you need more info please ask me!!

It would be tremendously helpful if you would post all relevant information at one time, rather than in piecemeal portions.

If you would take one moment to forget about Eclipse, and focus on the issue with the compiler, then perhaps we could solve your problem.  For now, post in its entirety the output that is displayed in the "CDT Build Console".... please no snapshots... just cut/paste the text into a formatted CODE block.

---

### Post by ofnuts on 2013-01-22
> **Warren Hill said:**
> Putting the header file in angle brackets

#include <utils/Utils.h>

tells the compiler that this is a standard header file so its probably looking in the wrong place

try 


#include "utils/Utils.h"

or 


#include "Utils.h"

May work better.  It will now look in the same directory as the other source files and should compile.

IIRC,

[LIST]
[*]#include'd files are always searched in both the current directory and some reference directories  (usually at least /usr/include and /opt/include)
[*]"utils/utils.h" tells the compiler to search the current directory first, and the reference directories next
[*]<utils/utils.h> tells the compiler to search the reference directories first, and the current directory last.
[/LIST]
One can think that Eclipse adds other designated projects to that list of "reference" directories (but these would show up as a "-I *project_directory*" in the gcc/g++ call).

---

### Post by dwhitney67 on 2013-01-22
> **ofnuts said:**
> IIRC,

[LIST]
[*]<utils/utils.h> tells the compiler to search the reference directories first, and the current directory last.
[/LIST]


When using the angle-brackets, the compiler will search the system directories, but not the current directory.  If using angle-brackets to reference a header file that is located somewhere outside the system directories, then then -I (dash-eye) compiler directive must be specified.

---

### Post by ofnuts on 2013-01-22
[I].
[/I]

---

### Post by indarkness on 2013-01-23
Hi all again,[B]

dwhitney67[/B] the thing is that I can compile it through linux termnial, but not using Eclipse... Indeed, I have found that the project is using autotools in eclipse for linking and configuring all the paths, myabe I should start reading  about autotools.

regards

---

### Post by dwhitney67 on 2013-01-23
I just noticed from one of your previous [posts]("http://ubuntuforums.org/showpost.php?p=12467980&postcount=6") that you are configuring Eclipse to use a path of <Project>/ibrcommon-0.8.0/tests/thread, yet in your code you are specifying an include directive for "thread/ThreadTest.h".

If you wish to keep the Eclipse configuration the same, then you should be including the file "ThreadTest.h" (w/o the leading 'thread' path).

The alternative is to leave the source code file alone, and modify Eclipse to use <Project>/ibrcommon-0.8.0/tests.

You may have other similar issues to this one.

---

### Post by indarkness on 2013-01-24
> **dwhitney67 said:**
> I just noticed from one of your previous [posts]("http://ubuntuforums.org/showpost.php?p=12467980&postcount=6") that you are configuring Eclipse to use a path of <Project>/ibrcommon-0.8.0/tests/thread, yet in your code you are specifying an include directive for "thread/ThreadTest.h".

If you wish to keep the Eclipse configuration the same, then you should be including the file "ThreadTest.h" (w/o the leading 'thread' path).

The alternative is to leave the source code file alone, **and modify Eclipse to use <Project>/ibrcommon-0.8.0/tests**.

You may have other similar issues to this one.

I will take a look to see if that is the reason,

Thanks again

EDIT: do you know how to make this reference you mention on Eclipse??

---

