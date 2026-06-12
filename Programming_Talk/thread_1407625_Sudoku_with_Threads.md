---
title: "Sudoku with Threads"
date: 2010-02-15
forum: Programming Talk
---

### Post by LKjell on 2010-02-15
Does anyone have any ideas on how to implements multi threads on solving Sudoku? Right now I have a recursive algorithm which checks the upper left square for possible figures and advance one square to the right and check there. If it fails it goes back one square and increase that value by one.

---

### Post by CptPicard on 2010-02-15
Well, just something quick off the top of my head... Sudoku seems like a constraint search problem, where choosing one value for one square will constrain the possibilities for the other squares, creating sub-search-problems...

More importantly, placing some value in any square will determine a completely disjoint (I think...) sub-search-tree for the future solution search for all solutions such that this value is set the way you just did. This means that you should be able to just dump the computation of such a subsearch onto some worker thread, and the task will be relatively isolated...

---

### Post by LKjell on 2010-02-15
> **CptPicard said:**
> Well, just something quick off the top of my head... Sudoku seems like a constraint search problem, where choosing one value for one square will constrain the possibilities for the other squares, creating sub-search-problems...

More importantly, placing some value in any square will determine a completely disjoint (I think...) sub-search-tree for the future solution search for all solutions such that this value is set the way you just did. This means that you should be able to just dump the computation of such a subsearch onto some worker thread, and the task will be relatively isolated...

If I am going to make a branch of each sub-search then I need to allocate a new grid for each thread since they cannot share the same working grid. Another thing is that I can risk one thread does not find anything. Hence if I have a limited threads there also might be some solution that will never be calculated. And if I have unlimited threads I will likely hang the whole system. Or I can have limited solved solution to be calculated.

thanks CptPicard. It is a risky operation so I will run programs on uni networks incase everything hangs.

---

### Post by Zugzwang on 2010-02-15
@OP: Have a look at "thread pooling" or "task pooling" which helps at distributing tasks to a limited number of threads. This might be what you want.

---

### Post by CptPicard on 2010-02-15
Yeah, I am thinking about having a separate working copy for each subproblem (after all, they do need their independent search states...).

Anyway, also try to make use of heuristics that prune the search tree efficiently... not sure what is beneficial, but for example one typical strategy is to always pick the next choice that constrains other future possibilities most (that is, removes possible values most from same row/column).

---

### Post by NovaAesa on 2010-02-15
I've written Sudoku solvers before, and if you are using a brute force search method you are doing it wrong (unless of course you are writing the program to practice you brute force algorithm skills).

If you write an algorithm that follows the same steps that a human follows when solving a Sudoku, most can be solved in only a few ms.

---

### Post by LKjell on 2010-02-15
> **NovaAesa said:**
> I've written Sudoku solvers before, and if you are using a brute force search method you are doing it wrong (unless of course you are writing the program to practice you brute force algorithm skills).

If you write an algorithm that follows the same steps that a human follows when solving a Sudoku, most can be solved in only a few ms.

And how does an average "human" solve sudoku problems?

---

### Post by Reiger on 2010-02-15
Average human would analyze the puzzel to find rows/columns/subsquares on which there is most data, and then attempt to solve the missing tiles in those rows/columns/subsquares first.

&#8220;Most data&#8221; means not just &#8220;I've got xyz in a row and abc in a column&#8221; but also what you learn from taking into account various tiles in the subsquares not part of the same row or column that directly limit the possible values in a blank tile.

---

### Post by NovaAesa on 2010-02-15
> **LKjell said:**
> And how does an average "human" solve sudoku problems?

Well, I determine which candidates are allowed in a square. You can keep track of this information with a 3 dimensional boolean array. If it so happens that in a certain square only a single number is allowed, then that number must go in that square. You can then deduce that all squares in that certain row, column and region cannot be the number just filled in. On harder sudokus this approach doesn't always work until you fill in some initial squares.

For this, you can use the reverse approach (which is a little more complex). If you look at a certain number which isn't in a certain row (or coloumn, or region), you can look at all the places where it might be able to go. If there is only one possible place, then that's where it goes.

Using methods such as these is many many times faster than running a brute force search algorithm (in this case I think you were proposing a backtracking algorithm if I understand correctly).

Think about the asymptotic complexity of the algorithm you are proposing and you will soon realise what the problem is.


EDIT: I can post some very old Visual Basic code of a sudoku solver that I did in high school if you would like. I'll be home and able to access my computer in a few hours.

---

### Post by CptPicard on 2010-02-16
NovaAesa, the constraint-solving approach (maybe using some sort of forward-checking of how constraints change when a number is assigned) is what I'm talking about up there. There's a good chapter on the techiques in "AI: A Modern Approach" for example.

---

### Post by NovaAesa on 2010-02-16
> **CptPicard said:**
> NovaAesa, the constraint-solving approach (maybe using some sort of forward-checking of how constraints change when a number is assigned) is what I'm talking about up there. There's a good chapter on the techiques in "AI: A Modern Approach" for example.

Ahh I see. What I said was more directed at the OP. Interesting that you mention that text book (Russell, S. and Norvig, P.: Artificial Intelligence - A Modern Approach), it's the prescribed text for one of the courses I'm going to do this semester.

---

### Post by LKjell on 2010-02-17
Well I am finish now but it went too slow for rank above 9. It was fun. I am using a modified thread pooling which set a maximum of queue threads and maximum of running threads

---

### Post by NovaAesa on 2010-02-17
I realise that you are finished your project, but here is the code I promised anyway. Bare in mind that I was in year 10 at the time... so the code isn't the best quality. Also, it was written in VB. Hopefully it will allow you to get an idea of what I was talking about before (if you are interested).



```

Attribute VB_Name = "modScripErase"
Option Explicit

Public Sub scriptErase(x As Integer, y As Integer) '**20/09/05
'Erases all corresponding scripts in that answer's row, column and region.
'Arguments x and y are the coordinates of the sqaure(answer) to be used.

Dim n As Integer

If answer(x, y) = 0 Then Exit Sub  'if square is unsolved then exit

For n = 1 To 9
    script(x, y, n) = False             'crosses out the scripts of that square
    script(n, y, answer(x, y)) = False  'crosses out equivelent scripts in that row
    script(x, n, answer(x, y)) = False  'crosses out equivelent scripts in that column.
Next n

'the section bellow crosses out the equivelent scripts in the region
'which contains the square (x,y).

For n = 1 To 9
    script(regionX(region(x, y), n), regionY(region(x, y), n), answer(x, y)) = False
Next n

End Sub

Public Sub kaijHanu(region As Integer) 'NEEDS FIXING
'looking at only 1 specific region, this sub firstly sees if there are only 2 of
'a certain script remaining. If so, then it finds out if there are in the same row
'or column. If this is so, it then goes to iliminate all other instances of this
'script in that row or column.

Dim s As Integer 'stores current script being checked
Dim n As Integer 'stores the current square in that region being processed
Dim count As Integer

64

For s = (s + 1) To 9

    count = 0
    For n = 1 To 9
        If script(regionX(region, n), regionY(region, n), s) = True Then
            count = count + 1
        End If
    Next n
    If count = 2 Then GoTo 61

Next s
Exit Sub

61
'this section finds out which square the two remaining scripts are in
Dim N1 As Integer 'stores the first square in which there is a remaining script
Dim N2 As Integer 'stores the second square in which there is a remaining script

For n = 1 To 9
    If script(regionX(region, n), regionY(region, n), s) = True Then
        N1 = n
        Exit For
    End If
Next n

For n = (N1 + 1) To 9
    If script(regionX(region, n), regionY(region, n), s) = True Then
        N2 = n
        Exit For
    End If
Next n

'this section finds out if the squares are in the the same row or column
If regionY(region, N1) = regionY(region, N2) Then GoTo 62 'same row
If regionX(region, N1) = regionX(region, N2) Then GoTo 63 'same column
Exit Sub

'this final section elimiates scripts in the row or column returned from
'the above three lines of code.

62
Dim x As Integer
For x = 1 To 9
    script(x, regionY(region, N1), s) = False
Next x
script(regionX(region, N1), regionY(region, N1), s) = True
script(regionX(region, N2), regionY(region, N2), s) = True
Exit Sub

63
Dim y As Integer
For y = 1 To 9
    script(regionX(region, N1), y, s) = False
Next y
script(regionX(region, N1), regionY(region, N1), s) = True
script(regionX(region, N2), regionY(region, N2), s) = True
GoTo 64

End Sub


```
```

Attribute VB_Name = "modSolvers"
Option Explicit


Public Sub onlyInRow(y As Integer) '**20/09/05
'Find the first square where there is only
'one of a certain script left in a row. The argument y
'refers to which row is being looked at.
'It then solves that sqaure and runs the scripterase sub.
Dim count As Integer
Dim s As Integer  'stores which script is being checked (Current Script)
Dim x As Integer  'stores the x-coord of the square being checked

For s = 1 To 9

    count = 0
    For x = 1 To 9
        If script(x, y, s) = True Then
            count = count + 1
        End If
    Next x
    If count = 1 Then GoTo 31
    
Next s
Exit Sub

31

For x = 1 To 9
    If script(x, y, s) = True Then
        answer(x, y) = s
        solved = solved + 1
        Call scriptErase(x, y)
        Exit Sub
    End If
Next x

MsgBox "error in private sub onlyinrow"

End Sub

Public Sub onlyInColumn(x As Integer) '**20/09/05
'Find the first square where there is only
'one of a certain script left in a colum. The argument x
'refers to which row is being looked at.
'It then solves that sqaure and runs the scripterase sub.
Dim count As Integer
Dim s As Integer  'stores which script is being checked (Current Script)
Dim y As Integer  'stores the x-coord of the square being checked

For s = 1 To 9

    count = 0
    For y = 1 To 9
        If script(x, y, s) = True Then
            count = count + 1
        End If
    Next y
    If count = 1 Then GoTo 41
    
Next s
Exit Sub

41

For y = 1 To 9
    If script(x, y, s) = True Then
        answer(x, y) = s
        solved = solved + 1
        Call scriptErase(x, y)
        Exit Sub
    End If
Next y

MsgBox "error in private sub onlyincolumn"

End Sub

Public Sub onlyInRegion(r As Integer) '**20/09/05
'Find the first square where there is only
'one of a certain script left in a region. The argument r
'refers to which region is being looked at.
'It then solves that sqaure and runs the scripterase sub.
Dim count As Integer
Dim s As Integer  'stores which script is being checked (Current Script)
Dim n As Integer  'stores which square "n" is being checked in region "r"

For s = 1 To 9

    count = 0
    For n = 1 To 9
        If script(regionX(r, n), regionY(r, n), s) = True Then
            count = count + 1
        End If
    Next n
    If count = 1 Then GoTo 51
    
Next s
Exit Sub

51

For n = 1 To 9
    If script(regionX(r, n), regionY(r, n), s) = True Then
        answer(regionX(r, n), regionY(r, n)) = s
        solved = solved + 1
        Call scriptErase(regionX(r, n), regionY(r, n))
        Exit Sub
    End If
Next n

MsgBox "error in private sub onlyinregion"

End Sub

Public Sub onlyInSquare(x As Integer, y As Integer)
'This sub solves the square (x,y) if there is only one script remaining in that square

Dim count As Integer
Dim s As Integer

For s = 1 To 9
    If script(x, y, s) = True Then count = count + 1
Next s

If count = 1 Then GoTo 71
Exit Sub

71

For s = 1 To 9
    If script(x, y, s) = True Then
        answer(x, y) = s
        solved = solved + 1
        Call scriptErase(x, y)
        Exit Sub
    End If
Next s

End Sub


```

---

