---
title: "C++ Manipulation of XML data."
date: 2010-02-15
forum: Programming Talk
---

### Post by Jonas thomas on 2010-02-15
Is there a generic C++ function that will replace everything between the "" directly in a string in one shot where I don't necessarily don't care what's between the ""
For Example.
<CodeLite_Project Name="Don't know or care" InternalType="Console">
Change to 
<CodeLite_Project Name="Whatever I want" InternalType="Console">

I was thinking that I could use the string::find [http://www.cplusplus.com/reference/string/string/find/]("http://www.cplusplus.com/reference/string/string/find/")
 to find the occurrence of the first """ and second """ using and then use the replace [http://www.cplusplus.com/reference/string/string/replace/]("http://www.cplusplus.com/reference/string/string/replace/")

If there's not something already, not a big deal. I can write a function. 
More curiosity than anything at the moment.

---

### Post by dwhitney67 on 2010-02-16
Yes, replace() would work.

I do not know if this is the 'safest' way to do this, but it may just work for you:
```

#include <fstream>
#include <string>
#include <iostream>

int main(int argc, char** argv)
{
   using namespace std;

   fstream inFile(argv[1], ios::in);
   string  line;

   while (getline(inFile, line))
   {
      // find where the "Name=" attribute starts
      const size_t pos1 = line.find("Name=");

      // if found...
      if (pos1 != string::npos)
      {
         const size_t pos2 = line.find("\" ", pos1 + 6);       // find the end of the string value

         line.replace(pos1 + 6, pos2 - (pos1 + 6), argv[2]);   // replace value with new string

         cout << line << endl;                                 // display result
      }
   }

   return 0;
}

```
Usage is:
```

g++ change.cpp -o change

./change orig.xml "Whatever I want"

```

---

### Post by Jonas thomas on 2010-02-16
Thanks,
That's along the lines of what I was thinking. I need to narrow it down slightly though since it will change too much.
I have a XML file I'm using as template to create projects:
Specifically what I need to mess with are the following:
<CodeLite_Project Name="Pr3-06" InternalType="Console">
<File Name="Pr3-6.cpp"/>

I think what I need to a function if the tag =="This" change the name= "to that"

Nothing out of the box?

Enough of the fun stuff... I'm off to the paying job. ;(





```

<?xml version="1.0" encoding="utf-8"?>
<CodeLite_Project Name="Pr3-06" InternalType="Console">
  <Description/>
  <Dependencies/>
  <Settings Type="Executable">
    <GlobalSettings>
      <Compiler Options="">
        <IncludePath Value="."/>
      </Compiler>
      <Linker Options="">
        <LibraryPath Value="."/>
      </Linker>
      <ResourceCompiler Options=""/>
    </GlobalSettings>
    <Configuration Name="Debug" CompilerType="gnu g++" DebuggerType="GNU gdb debugger" Type="" BuildCmpWithGlobalSettings="append" BuildLnkWithGlobalSettings="append" BuildResWithGlobalSettings="append">
      <Compiler Options="-g" Required="yes">
        <IncludePath Value="."/>
      </Compiler>
      <Linker Options="" Required="yes"/>
      <ResourceCompiler Options="" Required="no"/>
      <General OutputFile="$(IntermediateDirectory)/$(ProjectName)" IntermediateDirectory="./Debug" Command="./$(ProjectName)" CommandArguments="" WorkingDirectory="$(IntermediateDirectory)" PauseExecWhenProcTerminates="yes"/>
      <Debugger IsRemote="no" RemoteHostName="" RemoteHostPort="" DebuggerPath="">
        <PostConnectCommands/>
        <StartupCommands/>
      </Debugger>
      <PreBuild/>
      <PostBuild/>
      <CustomBuild Enabled="no">
        <CleanCommand/>
        <BuildCommand/>
        <PreprocessFileCommand/>
        <SingleFileCommand/>
        <MakefileGenerationCommand/>
        <ThirdPartyToolName>None</ThirdPartyToolName>
        <WorkingDirectory/>
      </CustomBuild>
      <AdditionalRules>
        <CustomPostBuild/>
        <CustomPreBuild/>
      </AdditionalRules>
    </Configuration>
    <Configuration Name="Release" CompilerType="gnu g++" DebuggerType="GNU gdb debugger" Type="" BuildCmpWithGlobalSettings="append" BuildLnkWithGlobalSettings="append" BuildResWithGlobalSettings="append">
      <Compiler Options="" Required="yes">
        <IncludePath Value="."/>
      </Compiler>
      <Linker Options="-O2" Required="yes"/>
      <ResourceCompiler Options="" Required="no"/>
      <General OutputFile="$(IntermediateDirectory)/$(ProjectName)" IntermediateDirectory="./Release" Command="./$(ProjectName)" CommandArguments="" WorkingDirectory="$(IntermediateDirectory)" PauseExecWhenProcTerminates="yes"/>
      <Debugger IsRemote="no" RemoteHostName="" RemoteHostPort="" DebuggerPath="">
        <PostConnectCommands/>
        <StartupCommands/>
      </Debugger>
      <PreBuild/>
      <PostBuild/>
      <CustomBuild Enabled="no">
        <CleanCommand/>
        <BuildCommand/>
        <PreprocessFileCommand/>
        <SingleFileCommand/>
        <MakefileGenerationCommand/>
        <ThirdPartyToolName>None</ThirdPartyToolName>
        <WorkingDirectory/>
      </CustomBuild>
      <AdditionalRules>
        <CustomPostBuild/>
        <CustomPreBuild/>
      </AdditionalRules>
    </Configuration>
  </Settings>
  <VirtualDirectory Name="src">
    <File Name="Pr3-6.cpp"/>
  </VirtualDirectory>
  <Dependencies Name="Debug"/>
</CodeLite_Project>





```


```

    // #include <stddef.h>
     #include <stdio.h>
     //#include <sys/types.h>
     #include <dirent.h> // This works in Posix compliant in linux but MS doesn't support it.
     #include <iostream>
     //#include <cstring>
	 #include <string>
	 #include <fstream>
	 using namespace std;


int main ()
{
 	   const char chaptersamplecode[]="//home/jonas/.codelite/CppClass/Chapter6/SampleCode/";
	   string ProjectTemplate = "//home/jonas/.codelite/CppClass/ProjectCreator/CodeLiteTemplate.project";
	   string projectNameString ="<CodeLite_Project Name=";
	   string fileNameString = "<File Name=";
	   char foldername[256];
	   
	   const string PROJECT_FOLDER_PREFIX("Pr6")  ;
	   DIR *dp;
       struct dirent *ep;
	   dp = opendir (chaptersamplecode); // Linux only
       size_t found;
	   string line;
	   string lineOutbound:
	   
	   if (dp != NULL)
         {
           while (ep = readdir (dp))
			{
				//ep->d_name; //only for linux
				string s(ep->d_name);//Well this has been covered either.
				
				if ((s.substr(0,int(PROJECT_FOLDER_PREFIX.length()))==PROJECT_FOLDER_PREFIX))
				{
					cout << "match"<<endl;
					//Need to dump a 
					// we need to open a input stream
				     
					ifstream myfile(ProjectTemplate.c_str() );
					
					//ifstream myfile("//home/jonas/.codelite/CppClass/ProjectCreator/CodeLiteTemplate.project");
					if (myfile.is_open())
					{
						while (! myfile.eof() )
						{
							getline (myfile,line);
							found=line.find(projectNameString);
							if (found!=string::npos)
							{
								cout << "!!!!!!!!!!!!!Need to do some string substitution here !!!!!!!!!!!!!!" << int(found) << endl;	
							}
							

							found=line.find(fileNameString);
							if (found!=string::npos)
							{
								cout << "!!!!!!!!!!!!!Need to do some more string substitution here !!!!!!!!!!!!!!" << int(found) << endl;	
							}



						
						
							cout << line << endl;
						
						
						
						}
						myfile.close();
					}
						else cout << "Unable to open file"; 
				}	
				else
					cout<<"No match"<<endl;
					
			
			
			} 
		   (void) closedir (dp);
         }
       else
         perror ("Couldn't open the directory");
 
}

```

---

### Post by MadCow108 on 2010-02-16
you can probably save same work by using regular expressions.

Unfortunately C++ does not yet natively support it but boost provides it:
[http://www.boost.org/doc/libs/1_42_0/libs/regex/doc/html/index.html](http://www.boost.org/doc/libs/1_42_0/libs/regex/doc/html/index.html)

(or use xml parser in the first place)

---

### Post by Jonas thomas on 2010-02-16
> **MadCow108 said:**
> you can probably save same work by using regular expressions.

Unfortunately C++ does not yet natively support it but boost provides it:
[http://www.boost.org/doc/libs/1_42_0/libs/regex/doc/html/index.html](http://www.boost.org/doc/libs/1_42_0/libs/regex/doc/html/index.html)

(or use xml parser in the first place)

Well part of this is to give myself an excerise to something pratical in the begineers C++ class I'm taking.

This boost stuff looks real real interesting. 
So... It looks opensource but not viral in liscensing.. Cool...

I was looking at the FAQ's real quick at it sounds like the libraries are portable... Another big plus..

I followed the link on C++ XML 
[http://cppxmlobj.sourceforge.net/]("http://cppxmlobj.sourceforge.net/")
I need to poke through the documetation a bit when I get  home.
Oh.. looks like C++ XMS will work in Linux,Mac but not support in windows.
Darn.. One of the reasons, I'm learning C++ is to develop cross platform skill sets.  I get the impression that VC++ goes out of there way to be better (read non portable)

I was running into portability issues with file io stuff. Seem's like Bill G. isn't interested in POSIX compliance.

---

### Post by dwhitney67 on 2010-02-16
One issue I have found, and may very well be wrong at this, is that the Boost XML library assumes that it will be parsing XML data was generated by the library itself.  It cannot parse XML data generated by another tool (or by hand).

Another popular XML parser tool thingy is the [Expat XML Parser]("http://expat.sourceforge.net/"), which was developed for C applications, but because of widespread use and devout users, also has C++ wrappers.

If you find that you can use Boost XML to parse your file, please let me know how you pulled it off.

P.S.  What I have done so far with Boost...

1.  Define data objects (classes);
2.  Populated these objects;
3.  Generated an XML file;
4.  Re-created new objects using the XML file.

As stated above, I have not been able to skip step 3 using an XML file created elsewhere.

---

### Post by MadCow108 on 2010-02-16
I'm not aware boost even has a xml parser.
Also it would be a pretty lousy one when it can't read xml (which is highly standardized) which it did not write itself.
Maybe you used some kind of beta version?

I also recommend expat, although I've only used it in C so far but it worked flawlessly for my task.

---

### Post by Jonas thomas on 2010-02-17
I tried to download cppxmlobj per the instructions for snicks and grinds.  I had to install cvs but for some reason I couldn't get a connection. Probably just as well this is way over my head for moment.

I reworked your suggestion to 
```

void replaceXmlNameValue(string& inputline, string ReplaceWith)
{
      // find where the "Name=" attribute starts
      const size_t pos1 = inputline.find("Name=");

      // if found...
      if (pos1 != (string::npos))
      {
         const size_t pos2 = inputline.find("\"", pos1 + 6);       // find the end of the string value

         inputline.replace(pos1 + 6, pos2 - (pos1 + 6), ReplaceWith);   // replace value with new string
      }
}

```
Seems to be working magnificantly..

Btw.. I find this very excellent language xref on strings on wikipedia.
[http://en.wikipedia.org/wiki/Comparison_of_programming_languages_%28string_functions%29#Format]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages_%28string_functions%29#Format")

I can do anything I with a string in vb.. Not so easy yet in C++.  This is been very helpful to me so far.  Thought it might be interest to some.
Next step... Need change the program to search my subfolder for cpp.files and insert them into the XML. Slow going but I think I'm starting to get the hang of this stuff. 
Thanks,

---

