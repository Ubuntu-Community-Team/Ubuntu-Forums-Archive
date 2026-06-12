---
title: "Problem with wxScintilla"
date: 2012-03-18
forum: Programming Talk
---

### Post by vanangamudi on 2012-03-18
Help me with this... I don't see any syntax error there...

[IMG]https://lh5.googleusercontent.com/-aIx5Q8H9DuM/T2TCIx8lnLI/AAAAAAAAARU/dPj8-2VAG80/s800/IDE01_02.png[/IMG]


Problem 1:
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
// External Lexer function definitions...
typedef void (EXT_LEXER_DECL *ExtLexerFunction)(unsigned int lexer, unsigned int startPos, int length, int initStyle,
                  char *words[], WindowID window, char *props);
typedef void (EXT_LEXER_DECL *ExtFoldFunction)(unsigned int lexer, unsigned int startPos, int length, int initStyle,
                  char *words[], WindowID window, char *props);
typedef void* (EXT_LEXER_DECL *GetLexerFunction)(unsigned int Index);
typedef int (EXT_LEXER_DECL *GetLexerCountFn)();
typedef void (EXT_LEXER_DECL *GetLexerNameFn)(unsigned int Index, char *name, int buflength);
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
scintilla/src/ExternalLexer.h:27: error: expected ‘)’ before ‘*’ token
scintilla/src/ExternalLexer.h:29: error: expected ‘)’ before ‘*’ token
scintilla/src/ExternalLexer.h:29: error: expected initializer before ‘*’ token
scintilla/src/ExternalLexer.h:30: error: expected ‘)’ before ‘*’ token
scintilla/src/ExternalLexer.h:31: error: expected ‘)’ before ‘*’ token
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Problem 2:
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
// Scintilla source code edit control
/** @file PropSetSimple.h
 ** A basic string to string map.
 **/
// Copyright 1998-2009 by Neil Hodgson <neilh@scintilla.org>
// The License.txt file describes the conditions under which this software may be distributed.

#ifndef PROPSETSIMPLE_H
#define PROPSETSIMPLE_H

#ifdef SCI_NAMESPACE
namespace Scintilla {
#endif

class PropSetSimple : public PropertyGet {
    void *impl;
    void Set(const char *keyVal);
public:
    PropSetSimple();
    virtual ~PropSetSimple();
    void Set(const char *key, const char *val, int lenKey=-1, int lenVal=-1);
    void SetMultiple(const char *);
    const char *Get(const char *key) const;
    char *Expanded(const char *key) const;
    char *ToString() const;
    int GetInt(const char *key, int defaultValue=0) const;
};

#ifdef SCI_NAMESPACE
}
#endif

#endif
----------------------------------------------------------------------------------------------------------------------------------------------------------
scintilla/src/PropSetSimple.h:15: error: expected class-name before ‘{’ token
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Problem 3:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
/// Sub-class of LexerModule to use an external lexer.
class ExternalLexerModule : protected LexerModule {
protected:
    ExtLexerFunction fneLexer;
    ExtFoldFunction fneFolder;
    int externalLanguage;
    char name[100];
public:
    ExternalLexerModule(int language_, LexerFunction fnLexer_,
        const char *languageName_=0, LexerFunction fnFolder_=0) : LexerModule(language_, fnLexer_, 0, fnFolder_){
        strncpy(name, languageName_, sizeof(name));
        name[sizeof(name)-1] = '\0';
        languageName = name;
    };
    virtual void Lex(unsigned int startPos, int lengthDoc, int initStyle,
                    WordList *keywordlists[], Accessor &styler) const;
    virtual void Fold(unsigned int startPos, int lengthDoc, int initStyle,
                    WordList *keywordlists[], Accessor &styler) const;
    virtual void SetExternal(ExtLexerFunction fLexer, ExtFoldFunction fFolder, int index);
};
-----------------------------------------------------------------------------------------------------------------------------------------------------------
scintilla/src/ExternalLexer.h:38: error: ‘ExtLexerFunction’ does not name a type
scintilla/src/ExternalLexer.h:39: error: ‘ExtFoldFunction’ does not name a type
scintilla/src/ExternalLexer.h:43: error: ‘LexerFunction’ has not been declared
scintilla/src/ExternalLexer.h:44: error: ‘LexerFunction’ has not been declared
scintilla/src/ExternalLexer.h:50: error: ‘Accessor’ has not been declared
scintilla/src/ExternalLexer.h:52: error: ‘Accessor’ has not been declared
scintilla/src/ExternalLexer.h:53: error: ‘ExtLexerFunction’ has not been declared
scintilla/src/ExternalLexer.h:53: error: ‘ExtFoldFunction’ has not been declared
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Problem 1 and 3 are related . right??

---

