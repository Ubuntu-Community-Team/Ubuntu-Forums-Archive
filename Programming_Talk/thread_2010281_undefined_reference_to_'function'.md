---
title: "undefined reference to 'function'"
date: 2012-06-25
forum: Programming Talk
---

### Post by hasanalikhattak on 2012-06-25
i am getting this compile error 
```
maser/mamas.o: In function `mamasReasoner::mamasReasoner()':
mamas.cc:(.text+0x9b): undefined reference to `NeoEnvironment::initFromNs(std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&)'
```

the code in NeoEnvironment header file is this

```
class NeoEnvironment {
  friend String Parser::evaluateString(const String &input);
public:
  static bool printDIG;  
  static void init();
  static void init(const String &outfilenm, const String &errfilenm);
  static void initFromNs(ostringstream&, ostringstream&, int = 1);
  static void initFromNs(ostream&, ostream&, int = 1);
  //static void init(ostream &out, ostream &err);  
  /////////////////////////////////////////////////////////
  //
  // Inserite da me
  //
  //static void init(ostream &out, ostream &err);
  static void evaluateCommand(const String &command);
  //
  /////////////////////////////////////////////////////////
  
  static void changeOutput(const String &outfn);
  static void cleanup();
  inline static void readFile(const String & filename);
  inline static void readFile();
  inline static void readXmlFile(const String & filename);
  inline static void readXmlFromMemory(const char* stringname, const char* name);
  static void readClient(int seconds, int port);
  static void readClient(int seconds);
  static int sock;
  static void print (const NeoObject &po);
  static void printInfo (const ClassicIndividual &ci);
  static void printInfo (const Concept &c);
  static void printInfo (const Role &r);
  static void printInfo (const Rule &r);
  static void printContents (const ClassicIndividual &ci);
  static void printContents (const Concept &c);

  static void writeKnowledgeBase(const KnowledgeBase &kb, const String &fn );
  static void writeKnowledgeBase(const String &fn);
  inline static ostream& outstream();
  inline static ostream& errstream();
private:
  static ostream *outstrm;
  static ostream *errstrm;
  NeoEnvironment();	// hiding
  ~NeoEnvironment() { if(sock!=0) close(sock); }	// hiding
};
```

---

### Post by dwhitney67 on 2012-06-25
> **hasanalikhattak said:**
> 
the code in NeoEnvironment header file is this

The code you have posted, albeit somewhat helpful, is not the implementation of the NeoEnvironment class; it is merely the declaration.

Please show the implementation, or better yet, investigate why the linker seems to think that you have not implemented:
```
NeoEnvironment::initFromNs(std::ostringstream&, std::ostringstream&)

```

P.S.  It is "obvious" from the header file that you posted that you have included a "using namespace std" directive in the header file.  You should never do that!

---

### Post by hasanalikhattak on 2012-06-26
i am using these classes and they have the implementation of functions inside it. so i think this is correct. but i dont know why it is giving this error

```

#ifndef NEOENVIRONMENT_H
#define NEOENVIRONMENT_H

#include <fstream>
#include <sstream>

using std::ofstream;
using std::ostringstream;

#include <NeoString.H>
#include <Parser.H>

class NeoObject;
class Description;
class Concept;
class Construct;
class ClassicConcept;
class ClassicConstruct;
class HostConcept;
class HostConstruct;
class ClassicIndividual;
class Role;
class Rule;
class KnowledgeBase;


//
// CLASS: NeoEnvironment
class NeoEnvironment {
  friend String Parser::evaluateString(const String &input);
public:
  static bool printDIG;  
  static void init();
  static void init(const String &outfilenm, const String &errfilenm);
  static void initFromNs(ostringstream&, ostringstream&, int = 1);
  static void initFromNs(ostream&, ostream&, int = 1);
  static void evaluateCommand(const String &command);
  static void changeOutput(const String &outfn);
  static void cleanup();
  inline static void readFile(const String & filename);
  inline static void readFile();
  inline static void readXmlFile(const String & filename);
  inline static void readXmlFromMemory(const char* stringname, const char* name);
  static void readClient(int seconds, int port);
  static void readClient(int seconds);
  static int sock;
  static void print (const NeoObject &po);
  static void printInfo (const ClassicIndividual &ci);
  static void printInfo (const Concept &c);
  static void printInfo (const Role &r);
  static void printInfo (const Rule &r);
  static void printContents (const ClassicIndividual &ci);
  static void printContents (const Concept &c);
  static void writeKnowledgeBase(const KnowledgeBase &kb, const String &fn );
  static void writeKnowledgeBase(const String &fn);
  inline static ostream& outstream();
  inline static ostream& errstream();
private:
  static ostream *outstrm;
  static ostream *errstrm;
  NeoEnvironment();	// hiding
  ~NeoEnvironment() { if(sock!=0) close(sock); }	// hiding
};

inline ostream& NeoEnvironment::outstream() {
  return *outstrm;
}

inline ostream& NeoEnvironment::errstream() {
  return *errstrm;
}

#include <ClassicIndividual.H>
#include <Concept.H>
#include <Kb.H>

inline void NeoEnvironment::readFile(const String &filename) {
  Parser::readFile(filename);
}

inline void NeoEnvironment::readXmlFile(const String &filename) {
	Parser::readXmlFile(filename);
}

inline void NeoEnvironment::readXmlFromMemory(const char *stringname, const char* name) {
	Parser::readXmlFromMemory(stringname, name);
}
```

and the parser class is as follows
```
#ifndef PARSER_H
#define PARSER_H

#ifndef _CPP_BACKWARD_FSTREAM_H
#define _CPP_BACKWARD_FSTREAM_H 1

#include <fstream>
using std::filebuf;
using std::ifstream;
using std::ofstream;
using std::fstream;
using std::streampos;

#ifdef _GLIBCPP_USE_WCHAR_T

using std::wfilebuf;
using std::wifstream;
using std::wofstream;
using std::wfstream;
using std::wstreampos;
#endif

#endif

#ifdef _MSC_VER
#include <sstrea>
#define DllImport __declspec( dllimport )
#define DllExport __declspec( dllexport )
#else
#include <sstream>
#define DllImport 
#define DllExport 
#endif
#include <NeoString.H>
#include <Symbol.H>
#include <Map.H>
#include <TellsTranslator.h>
#include <typedefs.H>
#include <NeoSet.H>
#include <NeoPtrObject.H>
#include <NeoObject.H>
#include <NeoEnvironment.H>
#include <DebugStream.H>
DEBUGSTREAM_VAR(dbout, PARSER);

using std::streambuf;
using std::stringstream;
class NeoObject;
class NeoForm;
class Inference;

class pstream : public istream {
public:
  pstream(streambuf*);
  int get();
  pstream& putback(char c);
  int lineNum;
};

inline int pstream::get() {
 int ch = istream::get();
 if (ch == '\n') lineNum++;
 return ch;
}

inline pstream& pstream::putback(char c) {
  if (c == '\n') lineNum--;
  istream::putback(c);
  return *this;
}

//
// CLASS: Parser
//
// DESCRIPTION:
//	Parser is a class that collects the various functions needed for 
//	parsing in NeoClassic.  There are also a few variables that are
//	specific to a particular parser.
//
//	The parser keeps track of a mapping from Symbols to NeoObjects to use 
//	as values of variables
//
class Parser {
//friend class match;  // by gr
public:
  Parser();
  Parser(istream& istr, const String &filename);
  Parser(stringstream& str);
  ~Parser();
  void readInput();
  static inline void setPrinting(Boolean b);
  static void set(const Symbol &varName, const NeoObject& obj);
  static void readFile(const String &filename);
  static void readXmlFile(const String &filename);
  static void readXmlFromMemory(const char * stringname, const char* name);
  NeoObject processForm();
private:
  enum Mode {NeoLispMode,NeoCMode};
  int getChar();
  void unGetChar(int);
  void skipWhite();
  String readString();
  String readWord(); 
  NeoObject readSymbol();
  NeoObject readNumber();
  NeoForm readForm();
  NeoObject readArgument();
  Boolean readFunctionArgs(List<NeoObject>& form);
  void printInconsistent(char * message, NeoPtrObject object,
			 const Inference & conflict, ostream &os);
  void printError(char * message, ostream &os);

  pstream stream;
  char commentLineChar; 
  String line;
  String fileName;
  Boolean errorFlag;
  Boolean printFlag;
  Mode mode;
  Boolean putback; // is there a character that was put back on the input
  int lastchar; // the last character read
  int inForm;	// number of form currently active

  static Boolean printing;	// print top-level values?
public:
  static Map< Symbol, NeoObject > variables;
  static String evaluateString(const String &input);

private:
  Parser(const Parser &);		// hiding
  Parser & operator=(const Parser &);	// hiding
  int operator==(const Parser &) const;	// hiding
};

//
// FUNCTION: void Parser::setPrinting(Boolean b)
//
// DESCRIPTION: turn on or off printing of top-level values
//
inline
void Parser::setPrinting(Boolean b) {
  printing = b;
}

inline
void Parser::readXmlFile(const String &filename) {
	ifstream innstream ( (const char*)filename );
	if (!innstream) {
		NeoEnvironment::errstream()<< "Error: could not open file " << filename	<< " for reading" << endl;
	} else {
		xmlDocPtr doc;
		doc = xmlReadFile((const char*)filename, NULL, XML_PARSE_NOBLANKS | XML_PARSE_NSCLEAN | XML_PARSE_NOWARNING);
		TellsTranslator translator(doc);
		stringstream xmlStream(stringstream::in | stringstream::out);
		Parser parser(translator.translate(xmlStream));
		dbout(DebugStream::med) << "readXmlFile::  created parser " << endl;
		parser.readInput();
	}
}
#endif
```

---

### Post by dwhitney67 on 2012-06-26
> **hasanalikhattak said:**
> i am using these classes and they have the implementation of functions inside it.


Where?  I see that you have _declared_ the following methods, but where are they _implemented_??
```

...
  static void initFromNs(ostringstream&, ostringstream&, int = 1);
  static void initFromNs(ostream&, ostream&, int = 1);
...

```
Perhaps it may be that you have implemented the methods, but that you are not compiling and/or linking the module that contains the implementation along with the module named mamas.cc

---

