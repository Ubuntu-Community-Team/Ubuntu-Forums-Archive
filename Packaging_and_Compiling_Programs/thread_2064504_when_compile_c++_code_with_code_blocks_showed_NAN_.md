---
title: "when compile c++ code with code blocks showed NAN but dev gave right answer."
date: 2012-09-29
forum: Packaging and Compiling Programs
---

### Post by selenaqd on 2012-09-29
Hi guys,

when I compile the follow c++ code with dev, it gave me right answer but with code blocks, it always said NAN. I have been using code blocks for a while, so I am quite get use to it, donot really want to change. do you have any idea why this is happening?

p.s. I also tried with other two computers to compile with code blocks, it showed the same result. 
Thanks advance!

Selena

//#include "..\std_lib_facilities.h"
 
const char let = 'L';
const char quit = 'Q';
const char print = ';';
const char number = '8';//t is a number token
const char name = 'a';
//----------------------------------------------------------------------
struct Token {
    char kind;
    double value;
    string name;
    Token(char ch)              :kind(ch),name(""),value(0) { cout << "Token: '" << ch << "'" << endl; }
    Token(char ch, double val)  :kind(ch),name(""),value(val) { cout << "Token: '" << ch << ",' value: " << val << endl; }
    Token(char ch, string n)    :kind(ch),name(n),value(0) { cout << "Token: '" << ch << ",' name: '" << n << "'" << endl; }
};
//----------------------------------------------------------------------------------
class Token_stream {
public:
//construct
    Token_stream() :full(0), buffer(0) { }
    Token get();
    void unget(Token t) { buffer=t; full=true; }
    void ignore(char);
private:
    bool full;
    Token buffer;
};
//---------------------------------------------------------------------------------------
 
 
Token Token_stream::get()
{
    if (full) {
        full=false;
        return buffer;
    }
 
    char ch;
    cin >> ch;
 
    switch (ch) {
        case '(':
        case ')':
        case '+':
        case '-':
        case '*':
        case '/':
        case '%':
        case ';':
        case '=':
            return Token(ch);
        case '.':
        case '0':
        case '1':
        case '2':
        case '3':
        case '4':
        case '5':
        case '6':
        case '7':
        case '8':
        case '9':
        {    
            cin.unget();
            double val;
            cin >> val;
            return Token(number,val);
        }
        default:
            if (isalpha(ch)) {
                string s;
                s += ch;
                while(cin.get(ch) && (isalpha(ch) || isdigit(ch)))
                    s+=ch;
                cin.unget();
                if (s == "let") return Token(let);
                if (s == "quit") return Token(quit);
                return Token(name,s);
            }
            error("Bad token");
    }
}
//----------------------------------------------------------------------------
void Token_stream::ignore(char c)
{
    if (full && c==buffer.kind) {
        full = false;
        return;
    }
    full = false;
 
    char ch;
    while (cin>>ch)
        if (ch==c) return;
}
//-------------------------------------------------------------------------
struct Variable {
    string name;
    double value;
    Variable(string n, double v) :name(n), value(v) { }
};
//------------------------------------------------------------------------
vector<Variable> names;
 
 
//----------------------------------------------------------------------
double get_value(string s)
{
    for (int i = 0; i< (int) names.size(); ++i)
        if (names[i].name == s) return names[i].value;
    error("get: undefined name ",s);
}
 
//---------------------------------------------------------------------
void set_value(string s, double d)
{
    for (int i = 0; i<= (int) names.size(); ++i)
        if (names[i].name == s) {
            names[i].value = d;
            return;
        }
    error("set: undefined name ",s);
}
//----------------------------------------------------------------------------------
bool is_declared(string s)
{
    for (int i = 0; i<(int)names.size(); ++i)
        if (names[i].name == s) return true;
    return false;
}
//--------------------------------------------------------------------------------
Token_stream ts;
//-------------------------------------------------------------------------
double expression();
//----------------------------
double primary()
{
    Token t = ts.get();
    switch (t.kind) {
    case '(':
    {
        double d = expression();
        t = ts.get();
        if (t.kind != ')')
            error("'(' expected");
        return d;
    }
    case '-':
        return - primary();
    case number:
    {
        cout << "Primary: number: " << t.value << endl;
        return t.value;
    }
    case name:
        return get_value(t.name);
    default:
        error("primary expected");
    }
}
//--------------------------------------------------------
double term()
{
    double left = primary();
 
    while(true) {
        Token t = ts.get();
        switch(t.kind) {
        case '*':
            left *= primary();
            break;
        case '/':
        {    double d = primary();
            if (d == 0) error("divide by zero");
            left /= d;
            break;
        }
        default:
            ts.unget(t);
            return left;
        }
    }
}
//-----------------------------------------------------------
double expression()
{
    double left = term();
    while(true) {
        Token t = ts.get();
        switch(t.kind) {
        case '+':
            left += term();
            break;
        case '-':
            left -= term();
            break;
        default:
            ts.unget(t);
            return left;
        }
    }
}
//-------------------------------------------------
double declaration()
{
    Token t = ts.get();
    if (t.kind != 'a') error ("name expected in declaration");
    string name = t.name;
    if (is_declared(name)) error(name, " declared twice");
    Token t2 = ts.get();
    if (t2.kind != '=') error("= missing in declaration of " ,name);
    double d = expression();
    names.push_back(Variable(name,d));
    return d;
}
//-------------------------------------------------------------------------
double statement()
{
    Token t = ts.get();
    switch(t.kind) {
    case let:
        return declaration();
    default:
        ts.unget(t);
        return expression();
    }
}
//-------------------------------------------------------------------
void clean_up_mess()
{
    ts.ignore(print);
}
 
//----------------------------------------------------------
const string prompt = "> ";
const string result = "= ";
//-----------------------------------------------------
void calculate()
{
    while(true) try {
        cout << prompt;
        Token t = ts.get();
        while (t.kind == print) t=ts.get();
        if (t.kind == quit) return;
        ts.unget(t);
        cout << result << statement() << endl;
    }
    catch(runtime_error& e) {
        cerr << e.what() << endl;
        clean_up_mess();
    }
}
//-------------------------------------------------
 
int _tmain(int argc, _TCHAR* argv[])
{    
    try {
        cout << "Calculator is online." << endl;
        calculate();
        keep_window_open();
        return 0;
    }
    catch (exception& e) {
        cerr << "exception: " << e.what() << endl;
        char c;
        while (cin >>c&& c!=';') ;
        return 1;
    }
    catch (...) {
        cerr << "exception\n";
        char c;
        while (cin>>c && c!=';');
        return 2;
    }
}

---

### Post by cogier on 2012-09-29
Err! You posted this in **Absolutely Beginner Talk**?!!

---

### Post by MG&amp;TL on 2012-09-29
> Hi guys,

when I compile the follow c++ code with dev, it gave me right answer but with code blocks, it always said NAN. I have been using code blocks for a while, so I am quite get use to it, donot really want to change. do you have any idea why this is happening?


The reason for this is likely that Code::Blocks uses a different compiler, compiler version, or default compiler flags than Dev-C++ (I am assuming by 'dev' you mean Dev-C++).

I'm not about to read through your code (please re-post in [CODE] tags, then I may re-consider :) ), but I do note you're using Bjarne Stroustrup's C++ guide (std_lib_facilities.h). I learned using this, it's a great guide. Good choice!

Have patience, and you'll get there.

---

### Post by Old_Grey_Wolf on 2012-09-29
Moved to Packaging and Compiling Programs.

---

