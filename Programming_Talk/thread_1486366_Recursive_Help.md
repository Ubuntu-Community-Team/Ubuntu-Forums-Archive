---
title: "Recursive Help"
date: 2010-05-17
forum: Programming Talk
---

### Post by concept08 on 2010-05-17
what i need is a recursive number generator i cannot have the function pick random numbers. i need it to go in order until all possibilities are taken into account

for example i would like the output to be something like this

1 1 1 1 1 1 1 1 1
1 1 1 1 1 1 1 1 2
1 1 1 1 1 1 1 1 3
1 1 1 1 1 1 1 1 4
1 1 1 1 1 1 1 2 1
1 1 1 1 1 1 1 2 2
1 1 1 1 1 1 1 2 3
1 1 1 1 1 1 1 2 4

basically i would like it to work something like that so the code recursively changed all the numbers so that every possible number combination is generated

9 total numbers for this example.
each number can be a range from 1-115 but for this example i used 1-4

here is some code that i made but it does not work how i would like it too

[PHP]donumbers(3,1,3,$sofar);
function donumbers($howmany, $low, $high, $sofar){
$n=0;
for($i=0;$i>=$low,$i<=$high;$i++){
$sofar_copy = $sofar;
$sofar_copy[$n] = $i;
$n++;
if ($howmany == 0){
$count = count($sofar_copy);
if($count == 3){
print_r($sofar_copy);
echo "<br>";
}// end if count statment
}else{
donumbers($howmany - 1, $low, $high , $sofar_copy);
}// end if howmany == 0 including else statment

}// end for statment
}// end function[/PHP] 

here is some output from the script and as you can see its not hitting every possible number combination as you can see it fails right from the start and never generates the sequence

1 1 1
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [2] => 2 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [1] => 1 [3] => 3 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [1] => 1 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [2] => 2 [3] => 3 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [0] => 0 [3] => 3 [1] => 1 )
Array ( [0] => 0 [3] => 3 [2] => 2 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [0] => 0 [2] => 2 )
Array ( [1] => 1 [0] => 0 [3] => 3 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [2] => 2 [0] => 0 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [2] => 2 [3] => 3 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [1] => 1 [3] => 3 [0] => 0 )
Array ( [1] => 1 [3] => 3 [2] => 2 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [0] => 0 [1] => 1 )
Array ( [2] => 2 [0] => 0 [3] => 3 )
Array ( [2] => 2 [1] => 1 [0] => 0 )
Array ( [2] => 2 [1] => 1 [3] => 3 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [2] => 2 [3] => 3 [0] => 0 )
Array ( [2] => 2 [3] => 3 [1] => 1 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [1] => 1 )
Array ( [3] => 3 [2] => 2 [1] => 1 )
Array ( [3] => 3 [2] => 2 [1] => 1 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [1] => 1 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [1] => 1 )
Array ( [3] => 3 [0] => 0 [1] => 1 )
Array ( [3] => 3 [0] => 0 [2] => 2 )
Array ( [3] => 3 [1] => 1 [0] => 0 )
Array ( [3] => 3 [1] => 1 [2] => 2 )
Array ( [3] => 3 [2] => 2 [0] => 0 )
Array ( [3] => 3 [2] => 2 [1] => 1 )

---

### Post by slavik on 2010-05-17
so you need a permutation generator ... have you tried wikipedia?

---

### Post by Lux Perpetua on 2010-05-18
I don't think you've thought this through. With 9 positions and 115 possible values for each, you're talking about more than 3 quintillion combinations. You can forget about iterating through all of them.

However, for academic interest, this is how you do it: ```
def generate(prefix, max, length):
    if length == 0:
        yield prefix
    else:
        for x in range(1, max+1):
            for s in generate(prefix + [x], max, length-1):
                yield s

for s in generate([], 115, 9):
    print s

```That's in Python. Hopefully the algorithm is clear, so you can port it to PHP or any other language.

---

