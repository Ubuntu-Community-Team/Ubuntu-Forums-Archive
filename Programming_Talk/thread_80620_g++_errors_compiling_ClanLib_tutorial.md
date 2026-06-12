---
title: "g++ errors compiling ClanLib tutorial ??"
date: 2005-10-22
forum: Programming Talk
---

### Post by kudu on 2005-10-22
What's going on here ?

kudu@ubuntu:~/tictactoe$ g++ TicTacToeApp.cpp TicTacToeGame.cpp -o `clanlib-config --cflags --libs` -lclanCore -lclanDisplay -lclanApp
TicTacToeGame.cpp: In member function ‘void TicTacToeGame::handleMousePress(const CL_Key&)’:
TicTacToeGame.cpp:78: warning: converting to ‘int’ from ‘const float’
TicTacToeGame.cpp:78: warning: converting to ‘int’ from ‘const float’
TicTacToeGame.cpp: In member function ‘void TicTacToeGame::computerMove()’:
TicTacToeGame.cpp:259: error: name lookup of ‘i’ changed for new ISO ‘for’ scoping
TicTacToeGame.cpp:232: error:   using obsolete binding at ‘i’
TicTacToeGame.cpp:265: warning: name lookup of ‘j’ changed
TicTacToeGame.cpp:253: warning:   matches this ‘j’ under ISO standard rules
TicTacToeGame.cpp:258: warning:   matches this ‘j’ under old rules

Is this to do with using g++ 4.0.2 ? I'm also using the repo ClanLib v6.5 but I don't think the tutorials have changed any between 6.5 and 7.8.

Help/advice appreciated.

Thanks!
kudu

---

### Post by kudu on 2005-10-22
Well I managed to solve that problem, now for the next...

kudu OUT

---

