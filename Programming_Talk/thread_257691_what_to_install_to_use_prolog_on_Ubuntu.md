---
title: "what to install to use prolog on Ubuntu?"
date: 2006-09-14
forum: Programming Talk
---

### Post by pixelmoon on 2006-09-14
I'm a compsci student starting to learn prolog.  In the notes, they have a section that explains a little of what the unix computers at school have.

[I]Using Prolog - UNIX

These instructions apply to using SB Prolog under the University's CCU UNIX systems. They will probably work with all other UNIX Prolog implementations, too.
1. Starting Prolog

    Type the command "prolog".

2. Creating a source file

    Use whatever editor you prefer. The prolog on Unix is the interpreter only, not an integrated environment, so you must use a separate editor. A Prolog file is an ordinary text file but its name should end with ".pro".

3. Consulting the rule base

    "Consulting" loads your Prolog source (facts and rules) from a text file into the interpreter.

    Type the query consult('filename'). from within prolog. Don't forget the quotes around the filename and the poeriod at the end. Use normal Unix file name conventions. For convenience, make sure that the files are in the current/working directory. (Use "cd" to get there before running prolog.)

4. Reconsulting the rule base after changes are made to it

    Use consult('filename'). again. Don't use reconsult. It doesn't work.

5. Entering queries

    Enter the query (no ?- needed) and press RETURN. If the solution was not just YES or NO, use ; then RETURN to see more solutions, or just RETURN to terminate the query.

6. Quitting

    Type the query halt. to prolog.[/I]

Should I try to use sb-prolog on ubuntu or is there something better?  If there is something better, I'd like to be assured that I'd have consistency with my laptop running my assignments and the system the marker will run it on.  Any help will be appreciated.  Thanks!

---

