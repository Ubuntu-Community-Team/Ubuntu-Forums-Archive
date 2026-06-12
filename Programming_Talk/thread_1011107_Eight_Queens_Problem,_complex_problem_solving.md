---
title: "Eight Queens Problem, complex problem solving"
date: 2008-12-14
forum: Programming Talk
---

### Post by luke77 on 2008-12-14
Hi guys,

I am a new programmer, and I'm doing it on my own so I'm finding that it's easy to develop bad habits. I came across the "eight queens" problem online and decided to write a script to solve it iteratively, without using recursion. I know it can be done with much less code with a recursive method, but I did it this way to try to develop good program design. My first try was a disaster; I tend to try to go as quickly as possible and not split up different methods into different functions, so when I come across a problem it's impossible to find out where it is. So for my second try I rewrote things, trying to separate processes into smaller methods (like makeBoard, isValidPos,etc.) instead of cramming it into one function. I also made a "Queens" class so that I don't have to pass the board to every single function. Anyways, I've spent quite a bit of time debugging "version two" and my code still is not working properly, so, I'd appreciate it if anyone could take a look to see where my code is hanging up. I'm also welcome to any comments or criticisms of my structure - like I said, I'm pretty much coming up with this on my own so I'm sure there is probably a better way to organize things. Thanks very much (code below).


Also, a bit of a related question: as I get more experience, I'm coming across complex problems for which the solution is not obvious and sometimes I can't figure it out at all. The Queens problem is not that difficult to figure out "how" to approach, at least with a inefficient method like this one, because there are several clear steps that you can break the problem down into. But some are not so obvious, and even for the Queens problem, a recursive solution is not obvious and I'm not sure that I'd be able to come up with it on my own. It seems like there are common patterns/approaches that programmers use, and when I read the ways advanced programmers have solved complex problems I think, "Wow, that was really smart"...but that doesn't help me when I come across a unique problem with a pattern I haven't seen before. Are there resources that cover common approaches to complex problems, or can anyone suggest ways to improve in this area?

Code for question 1:
```



class Queens:
   
   def __init__(self,sides):
      
      self.board=self.makeBoard(sides)
      self.length=sides
   def makeBoard(self,side):
       #returns 2X2 array with board dimensions
      return [[0]*side for i in range(side)]

   def isValidPos(self,row,col):
      try :
         self.board[row][col]
         return True
      except:
         return False
      
   def colClear(self,colNum):
      for row in range(len(self.board)):
         if self.board[row][colNum]:
            return False
      return True
      
      
   def diagClear(self,rowNum,colNum):
      for row in range(len(self.board)):
         dist=abs(rowNum-row)
         if not self.isValidPos(row,(colNum+dist)): 
            pass
         else: 
            if (self.board[row][colNum+dist]):
               return False
         if not self.isValidPos(row,(colNum-dist)):
            pass
         else:
            if (self.board[row][colNum-dist]):
               return False
      return True
   def rowClear(self,rowNum):
      for cell in self.board[rowNum]:
         if cell:
            return False
      return True
      
   def addQueen(self,rowNum,colNum):
      self.board[rowNum][colNum]="Q"
   
   def getQueenPos(self,rowNum):
      #Returns the column number of queen in a row. False if no queen.
      try:
         return self.board[rowNum].index("Q")
      except:
         return False
   def clearRow(self,rowNum):
      newRow=[0 for i in range(len(self.board))]
      self.board[rowNum]=newRow
      
      
   def findBestPos(self,rowNum,startCol):
      
      for cell in range(startCol,self.length):
         
         if self.isValidPos(rowNum,cell) and self.colClear(cell) and self.diagClear(rowNum,cell) and self.rowClear(rowNum):
            self.addQueen(rowNum,cell)
            return True
      return False
   def solved(self):
      for row in self.board:
         if "Q" not in row:
            return False
      return True
      
   def solveBoard(self):
      testrow=0
      testcol=0
      #Begin at square (0,0) and insert a queen in each row, testing for queens in the same column and diagonal. If there is no legal move, return to the previous row, get the position of its queen, remove the queen, and look for a valid position AFTER the previous position. If no new legal position is found, return to the previous row, etc.
      while not self.solved():
     
         if self.findBestPos(testrow,testcol):
            testrow+=1
            testcol=0
         else:
            testrow-=1
            testcol=self.getQueenPos(testrow)+1
            self.clearRow(testrow)
            
      for row in self.board:
         print row
board=Queens(8)
board.solveBoard()
```

---

### Post by Lux Perpetua on 2008-12-14
> **luke77 said:**
> Also, a bit of a related question: as I get more experience, I'm coming across complex problems for which the solution is not obvious and sometimes I can't figure it out at all. The Queens problem is not that difficult to figure out "how" to approach, at least with a inefficient method like this one, because there are several clear steps that you can break the problem down into. But some are not so obvious, and even for the Queens problem, a recursive solution is not obvious and I'm not sure that I'd be able to come up with it on my own. It seems like there are common patterns/approaches that programmers use, and when I read the ways advanced programmers have solved complex problems I think, "Wow, that was really smart"...but that doesn't help me when I come across a unique problem with a pattern I haven't seen before. Are there resources that cover common approaches to complex problems, or can anyone suggest ways to improve in this area?Of course: there are many textbooks on standard algorithms. The one I studied from was Sedgewick's *Algorithms in C*, which I'd say is "adequate." (The exposition is good; the code examples are not.) There's always Knuth's classic *The Art of Computer Programming*. 

Note that there is no list of programming techniques that will cover all interesting problems. You will sometimes need to solve a problem from scratch without being able to resort to a standard trick. 

Regarding your "8 queens" code, you really need to learn how to debug your own programs. Some tips that may help:

1. Don't write the entire program at once and then act surprised when it doesn't work. Write *and debug* one component at a time. (Obviously, it's too late for that now, but for future reference.) 

2. Make your program talk to you. If you don't have a decent debugger, intersperse debugging output throughout your program to tell you exactly what your program is doing.

---

### Post by mike_g on 2008-12-14
It looks as if your current algorithm will end up stepping back one row then stepping forward/back infinitely if there is a problem in the first rows. You might be able to solve the problem by adding a counter for each row. Once you have tried all eight positions on the last row, go back to the row before, replace the queen, increment that row's counter by the number of steps it took to find a valid place and move ahead. once you have exhausted all possible combination in the top rows (IE all their counters are set to 8 ) move down to the next lowest row and continue the search from a new position resetting the higher counters for the higher rows. Sorry if this sounds confusing - I havent tried this before, but I think it should work.

---

