---
title: "[SOLVED] Regular expression for a  function declaration  in Java"
date: 2008-04-10
forum: Programming Talk
---

### Post by fyplinux on 2008-04-10
Hi, I am seeking for a regular expression that could find all the function declarations of a class, or any C-style function declaration.

I have written up some code, but the regular expression seems a bit verbose, are there better solution?
[PHP]
 /*return true is line is a declaration of a function
     * parse by regular expression*/
    static boolean isFuncRegExp(String line) {
        int i, n;
        line.trim();

        //the prelimilary consideration, the reg exp is not capable for everything.
        if (line.length() == 0) {//empty line
            return false;
        }
        if (line.startsWith("//") || line.startsWith("/*") || !line.contains("(")) {//skip the comment
            return false;
        }
        String[] returnType = line.split("\\s");//the tokens of the line
        if (returnType.length == 0 || line.length() == returnType[0].length() || returnType[0].length() < 2) {
            return false;
        }
        for (i = 0; i < returnType.length; i++) {
            if (returnType[i].charAt(0) == '=') {//binding a value
                return false;
            }
        }

        //the first string should start with a letter
        String firstCh = line.substring(0, 1);
        if (!firstCh.matches("[a-zA-Z]")) {
            return false;
        }
        
      //a validName
        String validName = "[a-zA-Z0-9_]";       
        //validNames delimeted by white spaces
        String validNameSpace ="["+validName+"|"+validName+"(\\s)*"+"]";        
        //many occurence of the validNameSpace
        String Names = "("+validNameSpace+")*";        
        String regexp = Names+"("+"(.)*)";
        if(line.matches(regexp)){
            return true;
        }
        return false;
    }

[/PHP]

---

### Post by Zugzwang on 2008-04-11
The standard way of doing so would be to take a grammar file for C/C++/Java/whatever and use some tool like ANTRL or JavaCC to create a parser for you. There are some examples on ANTRL's and JavaCC's website. Using the parser, you can parse a source file and create a list of all identifiers you want.

---

