---
title: "Beginners Puzzle: Sodoku"
date: 2011-01-21
forum: Programming Talk
---

### Post by cprofitt on 2011-01-21
Alright... I want to see an increase the amount of puzzles and challenges in this forum so I figured I should lead by example and post one.

----
Sodoku Solver

Create a program that will solve a 4 x 4 sodoku puzzle. The user can input the puzzle and the program will output the solution.

I will let you choose how to get the input.

The output must be a series of numbers:

$: 4,1,2,3,2,3,4,1,1,2,3,4,3,4,1,2

----

Have fun!!

---

### Post by Queue29 on 2011-01-22
I have my input in a file called "sample.txt" like so:

```

000003017
015009008
060000000
100007000
009000200
000500004
000000020
500600340
340200000

```

I just took my code for Project Euler #96 and modified it for this. It solves the puzzles using recursive backtracking.

Written in Go.

```
// UFBPC, sudoku

package main

import "fmt"
import "strings"
import "io/ioutil"
import "strconv"

func main() {

	contents, err := ioutil.ReadFile("sample.txt")
	
	if err != nil {
	    fmt.Print("%s\n", err)
		panic("File IO Error!")
	}
	
	inFileStr := string(contents)
	splitted := strings.Split(inFileStr, "\n", -1)
	//fmt.Printf("Tokens: %d\n", len(splitted))

    s := splitted[0:9];
    //fmt.Printf("s.len: %d\n", len(s));    
    
		ss := NewSolver(s);
		//fmt.Print("-------\n")
		fmt.Printf("Unsolved: \n%s\n", ss.ToString())
		out, _ := ss.Solve()
		//ss.Solve()
		fmt.Printf("Solved: \n%s\n", DataStr(out))
		//fmt.Printf("val: %d\n", ss.TLCnum())
}

func DataStr(in [9][9]int) string {
    build := ""
    for r :=0; r<9; r++ {
        for c:=0; c<9; c++ {
            build += strconv.Itoa(in[r][c])
        }
        build += "\n"
    }
    return build
}

type Solver struct {
	data [9][9]int
	done bool
}

func (s *Solver) ToString() string {
	build := ""
	for r := 0; r < 9; r++ {
		for c := 0; c < 9; c++ {
			build += strconv.Itoa(s.data[r][c])
		}
		build += "\n"
	}
	return build
}

func NewSolver(sn []string) Solver {
    var ss Solver
    for j:=0; j<9; j++ {
        for i:=0; i<9; i++ {
            uk := (sn[j])[i]
            ss.data[j][i] = int(uk - 48)
        }
    }
    return ss
}

func (s *Solver) Solve() ([9][9]int, bool) {
    s.solve(0, 0)
    return s.data, true
}

func (s *Solver) checkRow(row, num int) bool {
    for col:=0; col<9; col++ {
        if s.data[row][col] == num {
            return false
        }
    }
    return true
}

func (s *Solver) checkCol(col, num int) bool {
    for row:=0; row<9; row++ {
        if s.data[row][col] == num {
            return false
        }
    }
    return true
}

func (s *Solver) checkBox(row, col, num int) bool {
    row = (row/3)*3
    col = (col/3)*3
    for r:=0; r<3; r++ {
        for c:=0; c<3; c++ {
            if s.data[row+r][col+c] == num {
                return false
            }
        }
    }
    return true
}

func (s *Solver) solve(row, col int) {
    if row > 8 {  // DONE
        s.done = true
        return
    }
    
    if s.data[row][col] != 0 {
        s.next(row, col)
    } else {
        for num:=1; num<10; num++ {
            if s.checkRow(row,num) && 
               s.checkCol(col, num) && 
               s.checkBox(row,col, num) {
                s.data[row][col] = num
                s.next(row, col)
            }
        }
        if !s.done {
            s.data[row][col] = 0
        }
    }
}

func (s *Solver) next(row, col int) {
    if col < 8 {
        s.solve(row, col+1)
    } else {
        s.solve(row+1, 0)
    }
}
```

Output:
```

[~/Code/UFBPC/sudoku] $ make run
./6.out
Unsolved: 
000003017
015009008
060000000
100007000
009000200
000500004
000000020
500600340
340200000

Solved: 
294863517
715429638
863751492
152947863
479386251
638512974
986134725
521678349
347295186

```

---

