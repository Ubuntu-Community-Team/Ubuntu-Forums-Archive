---
title: "perl - can't backtrack"
date: 2008-02-26
forum: Programming Talk
---

### Post by pedrotuga on 2008-02-26
I am having trouble using recursive backtracking.

This is a sudoku solver but once it finds a dead end it does not backtrack, it just returns.
The recursive call in inside the for cicle.
I included a 'next' in the code, but i don't know if it properly skis to the next iteration of the for cicle where the current function call is in.

There are some output examples in the code to illustrate the problem.

The function in use have been tested and work properly.

For convinience I uploaded this code in a pastebin to so one can read with syntax highlight.
[http://pastebin.com/f275a8fe0](http://pastebin.com/f275a8fe0)

```
$puzzleraw = "500000009019080750402000603004906500000000000006703800307000905085030120200000008";

#500000009
#019080750
#402000603
#004906500
#000000000
#006703800
#307000905
#085030120
#200000008

do "teste.pl";

@puzzle = &put_into_array($puzzleraw);

#solver function
&solve(@puzzle);

sub solve{
	
	&print_puzzle_array(@puzzle);

	@puzzle = @_;
	if (!have_empty_cells(@puzzle)){
		print "Hurray! Puzzle solved!\n";
		&print_puzzle_array(@puzzle);
		return 1;
	}
	$empty_cell_position = &find_first_empty_cell(@puzzle);
	$puzzle[0] = $empty_cell_position; #passed allong with the puzzle in the same array just to simplify
	@cell_possibilities = &get_possibilities(@puzzle);
	
	if ($#cell_possibilities == -1){next;} #can i use next in here to skip to the next iteration of the for cicle i am in?
	
	
	for $possible_value (@cell_possibilities){
		$puzzle[$empty_cell_position] = $possible_value;
		solve(@puzzle);
	}
}



######################################################################
#here goes a sample output
p@p-laptop:~/Desktop/perlscripts$ perl solver.pl

=========
500000009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========

=========
530000009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========

=========
538000009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========

=========
538100009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========

=========
538120009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========

=========
538124009
019080750
402000603
004906500
000000000
006703800
307000905
085030120
200000008
=========
p@p-laptop:~/Desktop/perlscripts$ 
```

---

### Post by PaulFr on 2008-02-29
```

sub solve {
   my @current_puzzle = @_;
   &print_puzzle_array(@current_puzzle);
   if (!have_empty_cells(@current_puzzle)) {
       print "Hurray! Puzzle solved!\n";
       return 1;
   }

   $empty_cell_position = &find_first_empty_cell(@current_puzzle);

# If you overwrite the first position of $current_puzzle,
# make sure you save the current value at
# that position, and restore it after the
# get_possibilities call. Does not seem
# necessary, but you know best.

   @cell_possibilities = &get_possibilities($empty_cell_position, @current_puzzle);
    
   for $possible_value (@cell_possibilities) {
       $current_puzzle[$empty_cell_position] = $possible_value;
       return 1 if (&solve(@current_puzzle) == 1);
   }
   return 0;
}

```

---

### Post by pedrotuga on 2008-02-29
The actual puzzle data is only in the elements 11 to 99 of the array.
I pass the position of the empty cell in the same array in order to keep it simple.

I figure out the problem, already.
I need to define the possibilities as a local variable with 'my'. Otherwise I will be left with rests from the last iteration.

Thank you anyway.

---

