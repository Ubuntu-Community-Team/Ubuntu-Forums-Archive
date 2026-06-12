---
title: "C++ Reading output from another program"
date: 2006-08-26
forum: Programming Talk
---

### Post by enigma_0Z on 2006-08-26
Using C++ code, how would I go about launching a program (for example ls) and then reading the output into a char* or std::string (Which would be better?)? I am talking about inside a C++ program, not using redirectors in the shell.

---

### Post by neilp85 on 2006-08-26
Take a look at the exec and fork functions in the standard library.

---

### Post by enigma_0Z on 2006-08-26
Dumb question but... Where would I "look" at the functions (other than poking around in the headers)?

Prolly a better question: Is there a good reference somewhere on the 'net?

---

### Post by neilp85 on 2006-08-26
I googled around a bit and this was the best page I could find:
[http://yolinux.com/TUTORIALS/ForkExecProcesses.html](http://yolinux.com/TUTORIALS/ForkExecProcesses.html)

I use the fork, execvp, pipe and some other functions to invoke in the chess game I'm working on to invoke gnuchess. Most of the code I found on the internet and only slightly modified it to work with our project. Here's some sample code to give you a basic idea of how we use them:
```
int m_to[2]
int m_from[2]

//Start GnuChess
void runChessEngine()
{
    pipe( m_to );
    pipe( m_from );

    if (fork() == 0) {
        // Child Process
        nice( 20 );
        dup2( m_to[0], 0 );
        dup2( m_from[1], 1 );
        close( m_to[0] );
        close( m_to[1] );
        close( m_from[0] );
        execvp( "gnuchess", NULL );
        cerr << "Couldn't run gnuchess" << endl;
    }
    write( m_to[1], "xboard\n", 7);
}

//Get the move from GnuChess
BoardMove getMove()
{
    string output;
    char c;
    while ( output.substr(0, 11) != "My move is:") {
        output = "";
        while ( read( m_from[0], &c, 1 ) ) {
            if ( c == '\n' )
                break;
            output += c;
        }
    }
    output = output.substr(12, 5);

    // Construct a BoardMove from the move string.
    stringstream oss(output);
    int rank;

    oss >> c;
    oss >> rank;
    BoardPosition origin(c, rank);

    oss >> c;
    oss >> rank;
    BoardPosition dest(c, rank);

    Board b = cgs.getBoard();
    return BoardMove move(origin, dest);
}

// Send your move to GnuChess
void sendMove(const BoardMove & move)
{
    string movestr = "";
    movestr += move.origin().filec();
    movestr += '0' + move.origin().rank();
    movestr += move.dest().filec();
    movestr += '0' + move.dest().rank();
    movestr += '\n';

    write( m_to[1], movestr.c_str(), 5);
}
```
It's been a while since that code was written and I don't remember what all the setup function calls do. Hopefully this can get you started though.

---

### Post by enigma_0Z on 2006-08-27
Thank you very much. That was exactly what I needed.

---

### Post by LordHunter317 on 2006-08-27
Assuming the command you're not running is complicated, you can just use popen().  Install manpages-dev and use 'man popen'.

---

### Post by neilp85 on 2006-08-27
Thanks for that info about the development manpages, I never knew about those. Quick question, what libraries does this include docs for? The package description doesn't say.

---

