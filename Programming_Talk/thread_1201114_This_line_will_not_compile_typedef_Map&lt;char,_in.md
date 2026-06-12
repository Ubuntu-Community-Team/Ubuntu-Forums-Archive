---
title: "This line will not compile: typedef Map&lt;char, int &gt; Datatypes;"
date: 2009-06-30
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-06-30
This works:

typedef int Datatypes;

This does not:

typedef Map<char, int > Datatypes;

Here is the code:

[PHP]
#include <fstream>
#include "yaml.h"
#include <iostream>
#include <Map>
#include <String>

using namespace std;

typedef Map<char, int> Datatypes;

struct Config
{
	Datatypes datatypes;
};


int main()
{


    return 0;
}
[/PHP]

ERROR Message:
[PHP]
yamlexample.cc:9: error: expected init-declarator before '<' token
yamlexample.cc:9: error: expected `,' or `;' before '<' token
yamlexample.cc:13: error: `Datatypes' does not name a type
make: *** [yamlexample] Error 1
[/PHP]

Can someone tell me why this does not work:

typedef Map<char, int > Datatypes;

---

### Post by dwhitney67 on 2009-06-30
The header files for String and Map should be string and map, respectively.

Similar for your declaration of the Map... that should be map, with a lowercase 'm'.

---

### Post by SNYP40A1 on 2009-06-30
> **dwhitney67 said:**
> The header files for String and Map should be string and map, respectively.

Similar for your declaration of the Map... that should be map, with a lowercase 'm'.

Thanks dwhitney, that fixed it.  I have another problem though, encountered when trying to overload the >> operator.  Here's my code:

[PHP]
#include <fstream>
#include "yaml.h"
#include <iostream>
#include <map>
#include <string>

using namespace std;

typedef map<string, map<string, string> > Datatypes;

struct Config
{
	Datatypes datatypes;
};

void operator >> (const YAML::Node& node, Config& config)
{
    node["datatype"] >> config.datatypes;
}

void operator >> (const YAML::Node& node, Datatypes& datatypes)
{
	// for(YAML::Iterator it=node.begin();it!=node.end();++it) 
	// {
		// std::string key, value;
		// it.first() >> key;
		// std::cout << "Key: " << key << std::endl;
	// }
}

int main()
{
    std::ifstream fin("test.yaml");
    YAML::Parser parser(fin);
	Config config;
	
	if(!fin.good())
	{
		std::cout << "Fin is not good " << std::endl;
	}

	YAML::Node doc;
	parser.GetNextDocument(doc);
	doc >> config;


    return 0;
}

[/PHP]

Only thing wrong with it is this one line:

node["datatype"] >> config.datatypes;

If you comment that out it compiles fine.  Otherwise, I get this error message:

[PHP]
./yaml-cpp-read-only/include/conversion.h: In static member function `static boo
l YAML::Converter<T>::Convert(const std::string&, T&) [with T = std::map<std::st
ring, std::map<std::string, std::string, std::less<std::string>, std::allocator<
std::pair<const std::string, std::string> > >, std::less<std::string>, std::allo
cator<std::pair<const std::string, std::map<std::string, std::string, std::less<
std::string>, std::allocator<std::pair<const std::string, std::string> > > > > >
]':
./yaml-cpp-read-only/include/conversion.h:15:   instantiated from `bool YAML::Co
nvert(const std::string&, T&) [with T = std::map<std::string, std::map<std::stri
ng, std::string, std::less<std::string>, std::allocator<std::pair<const std::str
ing, std::string> > >, std::less<std::string>, std::allocator<std::pair<const st
d::string, std::map<std::string, std::string, std::less<std::string>, std::alloc
ator<std::pair<const std::string, std::string> > > > > >]'
./yaml-cpp-read-only/include/node.h:102:   instantiated from `bool YAML::Node::R
ead(T&) const [with T = std::map<std::string, std::map<std::string, std::string,
 std::less<std::string>, std::allocator<std::pair<const std::string, std::string
> > >, std::less<std::string>, std::allocator<std::pair<const std::string, std::
map<std::string, std::string, std::less<std::string>, std::allocator<std::pair<c
onst std::string, std::string> > > > > >]'
./yaml-cpp-read-only/include/node.h:108:   instantiated from `void YAML::operato
r>>(const YAML::Node&, T&) [with T = Datatypes]'
yamlexample.cc:18:   instantiated from here
./yaml-cpp-read-only/include/conversion.h:22: error: no match for 'operator>>' i
n 'stream >> output'
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:87: note: candida
tes are: std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits
>::operator>>(std::basic_istream<_CharT, _Traits>&(*)(std::basic_istream<_CharT,
 _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:93: note:  std::b
asic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(s
td::basic_ios<_CharT, _Traits>&(*)(std::basic_ios<_CharT, _Traits>&)) [with _Cha
rT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:102: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
std::ios_base&(*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_trai
ts<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:111: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
bool&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:133: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
short int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:164: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
short unsigned int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:186: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:217: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
unsigned int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:239: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
long int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:261: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
long unsigned int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:284: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
long long int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:306: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
long long unsigned int&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:329: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
float&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:351: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
double&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:373: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
long double&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:395: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
void*&) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/bits/istream.tcc:417: note:  std::
basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(
std::basic_streambuf<_CharT, _Traits>*) [with _CharT = char, _Traits = std::char
_traits<char>]
./yaml-cpp-read-only/include/node.h:107: note:  void YAML::operator>>(const YAML
::Node&, T&) [with T = Datatypes]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/istream:692: note:  std::basic_ist
ream<char, _Traits>& std::operator>>(std::basic_istream<char, _Traits>&, signed
char*) [with _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/istream:687: note:  std::basic_ist
ream<char, _Traits>& std::operator>>(std::basic_istream<char, _Traits>&, unsigne
d char*) [with _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/istream:651: note:  std::basic_ist
ream<char, _Traits>& std::operator>>(std::basic_istream<char, _Traits>&, signed
char&) [with _Traits = std::char_traits<char>]
/usr/lib/gcc/i686-pc-cygwin/3.4.4/include/c++/istream:646: note:  std::basic_ist
ream<char, _Traits>& std::operator>>(std::basic_istream<char, _Traits>&, unsigne
d char&) [with _Traits = std::char_traits<char>]
make: *** [yamlexample] Error 1
[/PHP]

Any idea what is happening.  I interpret 

node["datatype"] >> config.datatypes; 

as applying the >> "function" to parameters node["datatype"] and config.datatypes.  Both 

[PHP]
node["datatype"];
[/PHP]

and 

[PHP]
config.datatypes;
[/PHP]

compile fine separately.

---

### Post by scourge on 2009-07-01
> **SNYP40A1 said:**
> Thanks dwhitney, that fixed it.  I have another problem though, encountered when trying to overload the >> operator.

Can you show the declaration of YAML::Node? What's the return type of YAML::Node::operator[](const std::string&)? And are you sure that you have defined operator>> for that type?

BTW, operators << and >> should always return a reference to the stream object, which would be YAML::Node& in this case.

---

### Post by SNYP40A1 on 2009-07-01
> **scourge said:**
> Can you show the declaration of YAML::Node? What's the return type of YAML::Node::operator[](const std::string&)? And are you sure that you have defined operator>> for that type?

BTW, operators << and >> should always return a reference to the stream object, which would be YAML::Node& in this case.

Here is node.h:

[PHP]
#pragma once

#include <string>
#include <ios>
#include <vector>
#include <map>
#include "parserstate.h"
#include "exceptions.h"
#include "iterator.h"
#include "conversion.h"

namespace YAML
{
	class Content;
	class Scanner;

	enum CONTENT_TYPE { CT_NONE, CT_SCALAR, CT_SEQUENCE, CT_MAP };

	class Node
	{
	public:
		Node();
		~Node();

		void Clear();
		void Parse(Scanner *pScanner, const ParserState& state);
		void Write(std::ostream& out, int indent, bool startedLine, bool onlyOneCharOnLine) const;

		CONTENT_TYPE GetType() const;

		// file location of start of this node
		int GetLine() const { return m_line; }
		int GetColumn() const { return m_column; }

		// accessors
		Iterator begin() const;
		Iterator end() const;
		unsigned size() const;

		// extraction of scalars
		bool GetScalar(std::string& s) const;

		// we can specialize this for other values
		template <typename T>
		bool Read(T& value) const;

		template <typename T>
		friend void operator >> (const Node& node, T& value);

		// just for maps
		template <typename T>
		const Node& GetValue(const T& key) const;

		template <typename T>
		const Node& operator [] (const T& key) const;

		const Node& operator [] (const char *key) const;

		// just for sequences
		const Node& operator [] (unsigned u) const;
		const Node& operator [] (int i) const;

		// for anchors/aliases
		const Node *Identity() const { return m_pIdentity; }
		bool IsAlias() const { return m_alias; }
		bool IsReferenced() const { return m_referenced; }

		// insertion
		friend std::ostream& operator << (std::ostream& out, const Node& node);

		// ordering
		int Compare(const Node& rhs) const;
		friend bool operator < (const Node& n1, const Node& n2);

	private:
		// shouldn't be copyable! (at least for now)
		Node(const Node& rhs);
		Node& operator = (const Node& rhs);

	private:
		void ParseHeader(Scanner *pScanner, const ParserState& state);
		void ParseTag(Scanner *pScanner, const ParserState& state);
		void ParseAnchor(Scanner *pScanner, const ParserState& state);
		void ParseAlias(Scanner *pScanner, const ParserState& state);

	private:
		int m_line, m_column;
		std::string m_anchor, m_tag;
		Content *m_pContent;
		bool m_alias;
		const Node *m_pIdentity;
		mutable bool m_referenced;
	};

	// templated things we need to keep inline in the header
	template <typename T>
	inline bool Node::Read(T& value) const {
		std::string scalar;
		if(!GetScalar(scalar))
			return false;

		return Convert(scalar, value);
	}

	template <typename T>
	inline void operator >> (const Node& node, T& value)
	{
		if(!node.Read(value))
			throw InvalidScalar(node.m_line, node.m_column);
	}

	template <typename T>
	inline const Node& Node::GetValue(const T& key) const
	{
		if(!m_pContent)
			throw BadDereference();

		for(Iterator it=begin();it!=end();++it) {
			T t;
			if(it.first().Read(t)) {
				if(key == t)
					return it.second();
			}
		}

		throw MakeTypedKeyNotFound(m_line, m_column, key);
	}

	template <typename T>
	inline const Node& Node::operator [] (const T& key) const
	{
		return GetValue(key);
	}

	inline const Node& Node::operator [] (const char *key) const
	{
		return GetValue(std::string(key));
	}
}
[/PHP]

and the C++ file:

[PHP]
#include "crt.h"
#include "node.h"
#include "token.h"
#include "scanner.h"
#include "content.h"
#include "parser.h"
#include "scalar.h"
#include "sequence.h"
#include "map.h"
#include "alias.h"
#include "iterpriv.h"
#include <iostream>

namespace YAML
{
	// the ordering!
	bool ltnode::operator ()(const Node *pNode1, const Node *pNode2) const
	{
		return *pNode1 < *pNode2;
	}

	Node::Node(): m_pContent(0), m_alias(false), m_pIdentity(this), m_referenced(true)
	{
	}

	Node::~Node()
	{
		Clear();
	}

	void Node::Clear()
	{
		delete m_pContent;
		m_pContent = 0;
		m_alias = false;
		m_referenced = false;
		m_anchor.clear();
		m_tag.clear();
	}

	void Node::Parse(Scanner *pScanner, const ParserState& state)
	{
		Clear();

		// an empty node *is* a possibility
		if(pScanner->empty())
			return;

		// save location
		m_line = pScanner->peek().line;
		m_column = pScanner->peek().column;

		ParseHeader(pScanner, state);

		// is this an alias? if so, its contents are an alias to
		// a previously defined anchor
		if(m_alias) {
			// the scanner throws an exception if it doesn't know this anchor name
			const Node *pReferencedNode = pScanner->Retrieve(m_anchor);
			m_pIdentity = pReferencedNode;

			// mark the referenced node for the sake of the client code
			pReferencedNode->m_referenced = true;

			// use of an Alias object keeps the referenced content from
			// being deleted twice
			Content *pAliasedContent = pReferencedNode->m_pContent;
			if(pAliasedContent)
				m_pContent = new Alias(pAliasedContent);
			
			return;
		}

		// now split based on what kind of node we should be
		switch(pScanner->peek().type) {
			case TT_SCALAR:
				m_pContent = new Scalar;
				break;
			case TT_FLOW_SEQ_START:
			case TT_BLOCK_SEQ_START:
			case TT_BLOCK_ENTRY:
				m_pContent = new Sequence;
				break;
			case TT_FLOW_MAP_START:
			case TT_BLOCK_MAP_START:
				m_pContent = new Map;
				break;
			default:
				break;
		}

		// Have to save anchor before parsing to allow for aliases as
		// contained node (recursive structure)
		if(!m_anchor.empty())
			pScanner->Save(m_anchor, this);

		if(m_pContent)
			m_pContent->Parse(pScanner, state);
	}

	// ParseHeader
	// . Grabs any tag, alias, or anchor tokens and deals with them.
	void Node::ParseHeader(Scanner *pScanner, const ParserState& state)
	{
		while(1) {
			if(pScanner->empty())
				return;

			switch(pScanner->peek().type) {
				case TT_TAG: ParseTag(pScanner, state); break;
				case TT_ANCHOR: ParseAnchor(pScanner, state); break;
				case TT_ALIAS: ParseAlias(pScanner, state); break;
				default: return;
			}
		}
	}

	void Node::ParseTag(Scanner *pScanner, const ParserState& state)
	{
		Token& token = pScanner->peek();
		if(m_tag != "")
			throw ParserException(token.line, token.column, ErrorMsg::MULTIPLE_TAGS);

		m_tag = state.TranslateTag(token.value);

		for(unsigned i=0;i<token.params.size();i++)
			m_tag += token.params[i];
		pScanner->pop();
	}
	
	void Node::ParseAnchor(Scanner *pScanner, const ParserState& state)
	{
		Token& token = pScanner->peek();
		if(m_anchor != "")
			throw ParserException(token.line, token.column, ErrorMsg::MULTIPLE_ANCHORS);

		m_anchor = token.value;
		m_alias = false;
		pScanner->pop();
	}

	void Node::ParseAlias(Scanner *pScanner, const ParserState& state)
	{
		Token& token = pScanner->peek();
		if(m_anchor != "")
			throw ParserException(token.line, token.column, ErrorMsg::MULTIPLE_ALIASES);
		if(m_tag != "")
			throw ParserException(token.line, token.column, ErrorMsg::ALIAS_CONTENT);

		m_anchor = token.value;
		m_alias = true;
		pScanner->pop();
	}

	void Node::Write(std::ostream& out, int indent, bool startedLine, bool onlyOneCharOnLine) const
	{
		// If using an anchor or tag for the whole document, document start
		// must be explicit
		bool indicateDocStart = (indent == 0);

		// write anchor/alias
		if(m_anchor != "") {
			if (indicateDocStart) {
				out << "--- ";
				indicateDocStart = false;
			}

			if(m_alias)
				out << "*";
			else
				out << "&";
			out << m_anchor << " ";
			startedLine = true;
			onlyOneCharOnLine = false;
		}

		// write tag
		if(m_tag != "") {
			if (indicateDocStart) {
				out << "--- ";
				indicateDocStart = false;
			}

			// put the tag in the "proper" brackets
			if(m_tag.substr(0, 2) == std::string("!<") && m_tag.substr(m_tag.size() - 1) == std::string(">"))
				out << m_tag << " ";
			else
				out << "!<" << m_tag << "> ";
			startedLine = true;
			onlyOneCharOnLine = false;
		}

		if(!m_pContent)
			out << "\n";
		else
			m_pContent->Write(out, indent, startedLine, onlyOneCharOnLine);
	}

	CONTENT_TYPE Node::GetType() const
	{
		if(!m_pContent)
			return CT_NONE;

		if(m_pContent->IsScalar())
			return CT_SCALAR;
		else if(m_pContent->IsSequence())
			return CT_SEQUENCE;
		else if(m_pContent->IsMap())
			return CT_MAP;
			
		return CT_NONE;
	}

	// begin
	// Returns an iterator to the beginning of this (sequence or map).
	Iterator Node::begin() const
	{
		if(!m_pContent)
			return Iterator();

		std::vector <Node *>::const_iterator seqIter;
		if(m_pContent->GetBegin(seqIter))
			return Iterator(new IterPriv(seqIter));

		std::map <Node *, Node *, ltnode>::const_iterator mapIter;
		if(m_pContent->GetBegin(mapIter))
			return Iterator(new IterPriv(mapIter));

		return Iterator();
	}

	// end
	// . Returns an iterator to the end of this (sequence or map).
	Iterator Node::end() const
	{
		if(!m_pContent)
			return Iterator();

		std::vector <Node *>::const_iterator seqIter;
		if(m_pContent->GetEnd(seqIter))
			return Iterator(new IterPriv(seqIter));

		std::map <Node *, Node *, ltnode>::const_iterator mapIter;
		if(m_pContent->GetEnd(mapIter))
			return Iterator(new IterPriv(mapIter));

		return Iterator();
	}

	// size
	// . Returns the size of this node, if it's a sequence node.
	// . Otherwise, returns zero.
	unsigned Node::size() const
	{
		if(!m_pContent)
			return 0;

		return m_pContent->GetSize();
	}

	const Node& Node::operator [] (unsigned u) const
	{
		if(!m_pContent)
			throw BadDereference();

		Node *pNode = m_pContent->GetNode(u);
		if(pNode)
			return *pNode;

		return GetValue(u);
	}

	const Node& Node::operator [] (int i) const
	{
		if(!m_pContent)
			throw BadDereference();

		Node *pNode = m_pContent->GetNode(i);
		if(pNode)
			return *pNode;

		return GetValue(i);
	}

	bool Node::GetScalar(std::string& s) const
	{
		if(!m_pContent)
			return false;
		return m_pContent->GetScalar(s);
	}

	std::ostream& operator << (std::ostream& out, const Node& node)
	{
		node.Write(out, 0, false, false);
		return out;
	}

	int Node::Compare(const Node& rhs) const
	{
		// Step 1: no content is the smallest
		if(!m_pContent) {
			if(rhs.m_pContent)
				return -1;
			else
				return 0;
		}
		if(!rhs.m_pContent)
			return 1;

		return m_pContent->Compare(rhs.m_pContent);
	}

	bool operator < (const Node& n1, const Node& n2)
	{
		return n1.Compare(n2) < 0;
	}
}
[/PHP]

The project was checked out from here:

[http://code.google.com/p/yaml-cpp/](http://code.google.com/p/yaml-cpp/)

---

### Post by SNYP40A1 on 2009-07-01
Also, I am basically trying to follow this example as a guide:

[http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument](http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument)

---

### Post by dwhitney67 on 2009-07-01
You've posted a lot of code, and unfortunately I do not have the luxury/time to pour over it all.  But tell us, is what I have below the gist of what you are trying to accomplish?

```

#include <map>
#include <string>
#include <iostream>

class Node
{
public:
   Node() {}

   const Node& operator[](const std::string& name) const;

   template <typename T>
   friend void operator>>(const Node& node, T& value);
};

const Node& Node::operator[](const std::string& name) const
{
   std::cout << "Inside Node::operator[]()." << std::endl;

   return *this;  // actually, should not be 'this', but a
                  // child of this, which is also a Node.
}

template <typename T>
void operator>>(const Node& node, T& value)
{
   std::cout << "Inside Node/T operator>>()." << std::endl;
}

struct Config
{
   typedef std::map<std::string, std::map<std::string, std::string> > DataTypes;

   DataTypes datatypes;
};

void operator>>(const Node& node, Config& config)
{
   std::cout << "Inside Node/Config operator>>()." << std::endl;

   node["datatype"] >> config.datatypes;
}

int main()
{
  Node   node;
  Config config;

  node >> config;
}

```

---

### Post by SNYP40A1 on 2009-07-01
> **dwhitney67 said:**
> You've posted a lot of code, and unfortunately I do not have the luxury/time to pour over it all.  But tell us, is what I have below the gist of what you are trying to accomplish?

```

#include <map>
#include <string>
#include <iostream>

class Node
{
public:
   Node() {}

   const Node& operator[](const std::string& name) const;

   template <typename T>
   friend void operator>>(const Node& node, T& value);
};

const Node& Node::operator[](const std::string& name) const
{
   std::cout << "Inside Node::operator[]()." << std::endl;

   return *this;  // actually, should not be 'this', but a
                  // child of this, which is also a Node.
}

template <typename T>
void operator>>(const Node& node, T& value)
{
   std::cout << "Inside Node/T operator>>()." << std::endl;
}

struct Config
{
   typedef std::map<std::string, std::map<std::string, std::string> > DataTypes;

   DataTypes datatypes;
};

void operator>>(const Node& node, Config& config)
{
   std::cout << "Inside Node/Config operator>>()." << std::endl;

   node["datatype"] >> config.datatypes;
}

int main()
{
  Node   node;
  Config config;

  node >> config;
}

```

Your code does work and compile and it is what I am trying to accomplish (although using YAML instead of your Node type).  All I am really trying to do is copy and slightly modify from this example:

[PHP]
// our data types
struct Vec3 {
    float x, y, z;
};

struct Power {
    std::string name;
    int damage;
};

struct Monster {
    std::string name;
    Vec3 position;
    std::vector <Power> powers;
};

// now the extraction operators for these types
void operator >> (const YAML::Node& node, Vec3& v)
{
    node[0] >> v.x;
    node[1] >> v.y;
    node[2] >> v.z;
}

void operator >> (const YAML::Node& node, Power& power)
{
    node["name"] >> power.name;
    node["damage"] >> power.damage;
}

void operator >> (const YAML::Node& node, Monster& monster)
{
    node["name"] >> monster.name;
    node["position"] >> monster.position;
    const Node& powers = node["powers"];
    for(unsigned i=0;i<power.size();i++) {
        Power power;
        powers[i] >> power;
        monster.powers.push_back(power);
    }
}

// ... and here's how we'll read our document
// (let's say our document has a bunch of monsters)
YAML::Node doc;    // already parsed
for(unsigned i=0;i<doc.size();i++) {
    Monster monster;
    doc[i] >> monster;
    // do something with this monster
}
[/PHP]
([http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument](http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument))

I don't see how what I am doing is any different than what they are trying to do.  The only difference that I see between your code and mine is that you are using a template.

---

### Post by SNYP40A1 on 2009-07-01
I found that this compiles fine:

[PHP]
#include <fstream>
#include "yaml.h"
#include <iostream>
#include <map>
#include <string>

using namespace std;

typedef map<string, map<string, string> > Datatypes;

struct Config
{
	Datatypes datatypes;
};

void operator >> (const YAML::Node& node, Config& config)
{
    //node["datatype"] >> config.datatypes;
}

void operator >> (const YAML::Node& node, Datatypes& datatypes)
{

}

int main()
{
    std::ifstream fin("test.yaml");
    YAML::Parser parser(fin);
	Config config;
	
	if(!fin.good())
	{
		std::cout << "Fin is not good " << std::endl;
	}

	YAML::Node doc;
	parser.GetNextDocument(doc);
	//doc >> config;
	doc["datatype"] >> config.datatypes;

    return 0;
}
[/PHP]

But this does not:

[PHP]
#include <fstream>
#include "yaml.h"
#include <iostream>
#include <map>
#include <string>

using namespace std;

typedef map<string, map<string, string> > Datatypes;

struct Config
{
	Datatypes datatypes;
};

void operator >> (const YAML::Node& node, Config& config)
{
    node["datatype"] >> config.datatypes;
}

void operator >> (const YAML::Node& node, Datatypes& datatypes)
{

}

int main()
{
    std::ifstream fin("test.yaml");
    YAML::Parser parser(fin);
	Config config;
	
	if(!fin.good())
	{
		std::cout << "Fin is not good " << std::endl;
	}

	YAML::Node doc;
	parser.GetNextDocument(doc);
	doc >> config;


    return 0;
}
[/PHP]

Only difference is 2 lines, doc >> config; and node["datatype"] >> config.datatypes;  I don't know why and doc["datatype"] >> config.datatypes; works when called from main, but node["datatype"] >> config.datatypes; does not work when called inside the function above.  doc and node are both the same type.

---

### Post by dwhitney67 on 2009-07-01
As you are aware, the example I provided earlier works, however I did not provide proper implementation for the following two methods:
```

const Node& Node::operator[](const std::string& name) const
{
   std::cout << "Inside Node::operator[]()." << std::endl;

   return *this;  // actually, should not be 'this', but a
                  // child of this, which is also a Node.
}

template <typename T>
void operator>>(const Node& node, T& value)
{
   std::cout << "Inside Node/T operator>>()." << std::endl;
}

```

The first method should be easy for you to implement, because I believe you already have the implementation for the operator[] method.

The second method requires a little more thought.  You will need to do whatever it is that you require to extract data from your Node object and insert it into your STL map.  Don't expect the operator>> to offer this.

So, just for instance, if your Node object had a method called getString(), then something like this might work:
```

const std::string str = node.getString();

value.insert(make_pair(str, make_pair(str, str)));

```
Of course, you probably wouldn't want to use the same string 3 times for the value inserted into the map.  You also must be aware that you are also compromising the portability of the method to work with only STL maps of type DataType.

Personally I would suggest that you add some public methods to the DataType structure.  Better yet, steer clear of using a template method for operator>>() in Node, because it would be difficult for you to use it for "any" object; it looks like you are coupling it too closely with DataType.

---

### Post by SNYP40A1 on 2009-07-01
dwhitney67, I appreciate your response and I think I know how to implement the methods.  What I do not understand is concisely represented in the last post that I made.  The >> operator works in one case (inside main), but not another (when called from inside another function).  The datatypes involved are the same so the same operator (>>) function that I overloaded should be used for both cases.  But I don't understand why I get the lengthy compile error in one case, but it compiles fine in another.  I think it has something to do with passing a const YAML::Node by reference...but I don't see it.

---

### Post by dwhitney67 on 2009-07-01
Check to see that you are implementing your overloaded operator>>() method within the YAML namespace.  Something like below:
```

//#include "yaml.h"

#include <fstream>
#include <iostream>
#include <map>
#include <string>

using namespace std;

typedef map<string, map<string, string> > Datatypes;

namespace YAML
{
class Node
{
public:
  Node() {}

  const Node& operator[](const string& str) const
  {
    return *this;
  }

  template <typename T>
  friend void operator>>(const Node& node, T& any);
};
}

struct Config
{
    Datatypes datatypes;
};


void operator>>(const YAML::Node& node, Config& config)
{
    node["datatype"] >> config.datatypes;
}

namespace YAML
{
template <typename T>
void operator >> (const YAML::Node& node, T& any)
{
   // you will need to implement what goes in here.
   //
   // The Node presumably has some information that you need to insert
   // into the object 'any'.  The object 'any' better have a generic
   // interface, or this method will not be usable for all objects T.

   cout << "**** I NEED TO IMPLEMENT SOMETHING HERE ****" << endl;
}
}

int main()
{
    Config     config;
    YAML::Node doc;

    doc >> config;
}

```

---

### Post by SNYP40A1 on 2009-07-01
I am not sure what I changed, but this seems to work now.  I guess no need to include the >> operators as part of the YAML namespace?  Anyways, thanks for your help dwhitney67, I am sure I will run into more issues as development continues.  I wish I could implement this project in Java :-(.  Here's the code that works:

[PHP]
#include <fstream>
#include "yaml.h"
#include <iostream>
#include <map>
#include <string>

using namespace std;

typedef map<string, map<string, string> > Datatypes;

struct Config
{
    Datatypes datatypes;
};

void operator >> (const YAML::Node& node, map<string, string>& typemap)
{
	for(YAML::Iterator it=node.begin();it != node.end();++it) {
		string key, value;
		it.first() >> key;
		it.second() >> value;
		typemap.insert(pair<string,string>(key, value));
		cout << key << "  " << value << endl;
	}
}

void operator >> (const YAML::Node& node, Datatypes& config)
{
	map<string, string> typemap;
	for(YAML::Iterator it=node.begin();it != node.end();++it) {
		std::string key, value;
		it.first() >> key;		
		std::cout << "Key: " << key <<  std::endl;
		it.second() >> typemap;
	}
}

void operator >> (const YAML::Node& node, Config& config)
{
	node["datatype"] >> config.datatypes;
} 

int main()
{
    std::ifstream fin("test.yaml");
    YAML::Parser parser(fin);
    Config config;
    
    if(!fin.good())
    {
        std::cout << "Fin is not good " << std::endl;
    }

    YAML::Node doc;
    parser.GetNextDocument(doc);
    doc >> config;

    return 0;
}  
[/PHP]

---

### Post by dwhitney67 on 2009-07-01
Are you not missing some code in the method below?  See the comment...
```

void operator >> (const YAML::Node& node, Datatypes& config)
{
    map<string, string> typemap;
    for(YAML::Iterator it=node.begin();it != node.end();++it) {
        std::string key, value;   // declaration for value is not needed!
        it.first() >> key;        
        std::cout << "Key: " << key <<  std::endl;
        it.second() >> typemap;

        // insert key/typemap pair into config map???
    }
}

```

---

