---
title: "Stumped"
date: 2008-09-22
forum: Programming Talk
---

### Post by luke77 on 2008-09-22
Hi everyone,

I'm new to the forums; I'm trying to teach myself programming starting with Python and I've only been programming for a few weeks. Someone suggested that I visit this forum and it looks like a great community. After reading through 2 tutorials on Python, I am basically trying to reinforce the material (so that I actually learn it), and it seems that the best way to do this is by doing problems/exercises. I have been working my way through the MIT opencourseware intro to programming course, at this link:

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm)

Please note that this is not my homework; I'm out of school and just trying to teach myself to program. I am stumped on problem number five, part two (and it looks like I will also be stumped on part 3).

Basically, I'm at a loss as to how to approach it. My first thought was to use some sort of nested for loop structure to iterate through each possible state combination, but I don't think this is possible, since a for loop would just test for, for instance, (state 1 and 2, state 1 and 3, state 1 and 4, etc.) and not (state 1 and 3, state 1 and 2 and 3, etc.). I could maybe make it work for a very small number of states, but if you are taking 10 states as arguments I don't see a way this could work. Also, the way the question is asked seems to imply that the new code will go after the existing code, and also that it will be only about five lines. I'm guessing that maybe some kind of recursion is required but I really don't know, and recursion is a new concept to me as well. I've posted the relevant part below but it's also available at the link. Thanks for any help.

Complete and test this function according to her specification below.
Note that she was using exhaustive
enumeration to compute the result. Your friend assured you that the
function needs no more than 5 additional
lines of code.

# Problem 2: Exhaustive enumeration
def finance_campaign_ee(budget, free_states):    """
  Takes a budget, in dollars, and a list of available states, as a
  list of dictionaries.

  Computes and returns the list of states that maximizes the total
  number of electoral votes such that these states can be acquired
  on the budget. Returns an empty list if no states can be acquired.

  """
  cheap_states=[]
  for s in free_states:
      if s['pop'] <= budget:
          cheap_states.append(s)

  # Base case
  if len(cheap_states)==0:
      res_list=[]
  # Recursive case
  else:
      curr_state=cheap_states[0]
      other_states=cheap_states[1:]

      inc_states=finance_campaign_ee( budget-curr_state['pop'],
                                       other_states)
      inc_states.append(curr_state)
      inc_evotes=total_evotes(inc_states)

      excl_states=finance_campaign_ee( budget, other_states )
      excl_evotes=total_evotes(excl_states)

      # ... your code goes here ...
      res_list   =    return res_list

---

### Post by luke77 on 2008-09-22
Oh yeah, one more thing: if anyone can suggest additional resources for exercises or problems that will help improve skills, I'd greatly appreciate it. I'm finding plenty of free tutorials and readings on programming, but it's kind of like learning calculus; that is, it doesn't do a whole lot to just read about the concepts, you really learn by working problems. Ideally I'd like to have problems akin to the exercises at the end of the chapter in a math book, with solutions that I can look at if stumped.

Thanks again.

---

### Post by pmasiar on 2008-09-22
You are absolutely right that you cannot learn programming by reading the books, but only by solving problems.

Check tutorials in my wiki, many with homeworks, and  plenty of training tasks. First 10 problems in Project Euler are pretty easy.

Homework for MIT students might be pretty hard, those are some of the smartest students on the planet: Average SAT score is around 1500 or so.

---

### Post by luke77 on 2008-09-24
Thanks. Anyone else, regarding this specific problem?

---

### Post by unutbu on 2008-09-25
The key to understanding recursion is to be presumptuous: assume you've already written the finance_campaign_ee function even though you haven't. Think of it as a black box: you stick in the free states (and a budget) and it returns the subset of free states which maximizes the votes.

Now think about what these lines do:
```

        inc_states=finance_campaign_ee( budget-curr_state['pop'],
                                        other_states)
        inc_states.append(curr_state)


```
versus
```

        excl_states=finance_campaign_ee( budget, other_states )

```
When you think of finance_campaign_ee as a black box, what information do you gain by running these commands? In words try to articulate what inc_states and excl_states represent.
Once you can do that, ask yourself if you had to give your friend an answer about which states to run in, would it be inc_states or excl_states? Or would you give her some other answer? This last question is perhaps the trickiest part to answer satisfactorily. Think about it hard and you'll know something nice.

If you'd like more hints, post.

---

### Post by nvteighen on 2008-09-25
The best way to learn to use recursion is to learn Scheme... :p

No, don't go for that language now, but it's quite actually true. I didn't really understand recursion until I got into the tail-recursion technique that's so common in Scheme.

The trick is basically is this, and is appliable to any language:
```

0. Give a name to your function.
1. Set a condition to stop the recursion and do something when that happens.
2. Prepare stuff for next recursion step
3. Recurse passing the stuff you prepared calling the function by it's name.

```

(Step 0 is not a joke. As the guys at [SICP]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/") say, in programming, you only have power over something when you know its name. Recursion on anonymous parts of code is somewhat difficult if not impossible)

That's called "tail-recursion", because recursion is the last thing you tell the function to do. Also, it sets the recursion as the thing the function is meant to do as "normal behaivor", leading it to stop just because of an exceptional condition.

The return value of a recursive function shouldn't be void; it should always return something you can hold in a variable that you then pass in the next recursion. And when you stop at step 1, you just return that variable that was holding the value. IMO, it's the easiest way to do it.

---

### Post by luke77 on 2008-09-25
Thanks, guys. I'm still missing it, though. To answer your post, unutbu, as I understand it, the first piece of code that you posted will return a list of states that can be "bought" under the given budget, beginning with the first state in the list and proceeding in order through the list. The second piece of code takes the remaining states (I think?) and runs the same recursive function on these states, presumably returning a list that can be bought, excluding the ones used in the first list. 

I am kind of confused about the second piece of code though, because it seems like when the finance_campaign_ee() recursion is run from this piece of code, it will run through the 

inc_states=finance_campaign_ee( budget-curr_state['pop'], other_states) 

line of code, which I guess ends up returning a list of possible states from the excluded states.

I don't see where this gets us, though. If I am correct so far, what is returned is a list of possible states starting from the start of the list in order until the money runs out. What we need, though, is this list, but then compare it to a list starting from state 1 and skipping state 2, and then trying 3...x, and then compare this list to a list starting from state 1, 2, and skipping state 3, and then trying 4...x. And THEN, skipping 2 AND 3, trying 4...x, etc. So that basically all possible combination are tried and the best possible result returned. I'm at a loss as to how to even go about this. 

Thanks again; this problem has been driving me crazy and it's especially frustrating that the answer is five lines of code!

---

### Post by unutbu on 2008-09-25
Suppose that all you know about finance_campaign_ee is that it returns the subset of states which maximize the votes. Whereever you see finance_campaign_ee, think about it in terms of this property. 

So when you run
```

inc_states=finance_campaign_ee( budget-curr_state['pop'], other_states)
```

inc_states is going to be a subset of other_states, with the special property that it maximizes the number of votes while spending no more than (budget-curr_state['pop']) dollars.

Here is a made-up example: I'm going to write my list of states like this
```

[PA, VA, MI, MA, NY]
``` instead of 
```

[{'evotes':21, 'name':'Pennsylvania', 'pop':12440621},  
 {'evotes':13, 'name':'Virginia', 'pop':7642884},
 ...
 ]
```

But I think you'll get the picture.

Let's suppose cheap_states=[PA, VA, MI, MA, NY]

Then curr_state = PA and other_states=[VA, MI, MA, NY]

(You might understand the code better if you regard this situation as arising because "your friend" comes to you and says, I am going to win PA. I don't care about the computer program, I am going to spend whatever it takes to win PA.)

Let's say the budget = 100 and the population of PA is 15. Then 
```

inc_states=finance_campaign_ee( budget-curr_state['pop'], other_states)
```

is the same as 
```

inc_states=finance_campaign_ee( 85, [VA, MI, MA, NY])
```

and this means that inc_states will be a subset of [VA, MI, MA, NY] with the property that it maximizes the number of votes attainable with 85 dollars. For the sake of concreteness, suppose inc_states is [MI, NY]. 

Then the next line of code 
```

inc_states.append(curr_state)
```

alters inc_states so that it is now [PA, MI, NY].

So inc_states tells you that winning [PA, MI, NY] is the best you can do on a budget of 100 given that you have to include PA. (Notice that we called finance_campaign_ee with a budget of 85 because 15 had to be committed to win PA.)

So now ask yourself, what does excl_states represent?

---

### Post by luke77 on 2008-09-26
I feel like an idiot because I am still not getting this. Thank you for taking the time to try to walk me through it. Let me try to respond using your theoretical scenario:

First, to address your final question, "what does excl_states represent", it now takes the remaining states (VA and MA), and returns the states that can be bought under the budget. So if VA+MA<100, it will be VA and MA. Am I right so far?

Okay. Now, a few things remain that I don't get. Sticking to your scenario, when you write:

> and this means that inc_states will be a subset of [VA, MI, MA, NY] with the property that it maximizes the number of votes attainable with 85 dollars. For the sake of concreteness, suppose inc_states is [MI, NY].

I don't see how you suppose that inc_states is [MI, NY]. I think if I assign values to each state it will be easier to understand where I'm coming from (I'm ignoring your inclusion of MI and NY as inc_states, for now, this is a totally new scenario). Let's say VA=35, MI=30 , MA=40 ,NY=55. We can look at this and see that the best choice of states is [MI,NY], because this will use exactly 85 dollars and return 85 votes. If we use the recursive function, though, it will return [VA,MI], because they are first in the list, both fit under the budget, and after their inclusion the budget will be down to 20, so that neither MA or NY will be included. Does this make sense? The optimal scenario is states 2 and 4, but since the function goes in order, it returns states 1 and 2. To truly find the best choice the program needs to test [VA,MI,MA,NY], [VA,MA,NY], [VA,MI,NY], [VA,NY], [MI,MA,NY], [MI,NY], [MA,NY], [NY]. I'm probably leaving out one or two, but you get the picture. My concern (or misunderstanding, perhaps) is that the function as it stands does not do this.

Also, although I think I understand what excl_states represents, as I described above, I don't understand its purpose.

---

### Post by pp. on 2008-09-26
You are trying to understand the partial code in procedural terms. Hence, your reasoning goes something like

that variable contains such-and-such, then this expression does -something- so that I expect the variable to increase...

I have found it very useful to trying such code in 'declarative' terms. My reasoning would run something like

That variable expresses the number of ... this function call stands for a set of ...

Let's apply this to the bit of code that has you stumped, finance_campaign_ee(budget, free_states):

According to the specification (which is given in the comments at the beginning of that function) we are to read 
```
A selection of the states in the list free_states that can be bought for the sum indicated by budget
```
whenever we see
```
finance_campaign_ee(budget, free_states)
```

Now let's try and understand the body of that function.

***cheap_states*** is a selection of the states in free_states where none of the states has a cost which exceeds the budget.

That's an optimisation, but it's reasonable. Any state which costs more than our budget can not possibly appear in the list of affordable states.

***curr_state*** is simply the first state in cheap_states, while
***other_states*** is a list with all but the first of cheap_States.

***inc_states*** is a selection of the states in ***other_states*** that can be bought for the budget which is left after buying ***current_state***.

***excl_states*** is a selection of the states in ***other_states*** that can be bought for all of the budget (i.e. if we don't buy ***current_state***).

Those two (inc_states and excl_states) are formed according to the rule I outlined above: we substituted the function call (finance_campaign_ee) by the phrase given above. 

***inc_evotes*** and ***excl_evotes*** are the numbers of electors bought with ***inc_states*** and ***excl_states***, respectively.

We now have reached the place in the function where you have to supply the remaining code. 

It should have become clear by now that the function to be completed invokes itself two times with all but one state and two different budgets for those. I have not commented the case when there are no more states left.

---

### Post by unutbu on 2008-09-26
> ... I am still not getting this. Thank you for taking the time to try to walk me through it.

You are welcome, and have no worries. We all start not knowing something, and the only way to learn it is to try. I am confident you will get it, and when you do you will know something quite beautiful.

[list]
[*]Regarding excl_states, you write

> First, to address your final question, "what does excl_states represent", it now takes the remaining states (VA and MA)...

Here we need to be careful: excl_states is defined this way:
      
```

  excl_states=finance_campaign_ee( budget, other_states )

```

Notice it is called with the second parameter being other_states.
other_states = [VA, MI, MA, NY], not [VA, MA]. So excl_states is the subset of [VA, MI, MA, NY] which maximizes votes, subject to the budget constraint.

[*]From your posts it appears you believe that finance_campaign_ee will grab as many states as possible from the beginning of the list. This is your key stumbling block. You are assuming this; it isn't written down in the partial code that was given. 

Release yourself from this assumption and instead assume that all you know about finance_campaign_ee is that it is a magical black box with the property that it returns a subset of states which maximizes votes, while staying within a budget. Do not assume anything else about finance_campaign_ee.

[*]The partial code given in finance_campaign_ee is a hint inviting you to solve the problem in a particular way. It happens to be different from the way you described in previous posts.

It's easier to understand if we suppose a concrete list of states. So again let's suppose 
cheap_states=[PA, VA, MI, MA, NY].

finance_campaign_ee is going to return the subset of [PA, VA, MI, MA, NY] which maximizes votes. 

Now ask yourself the question, "Is PA in the subset returned by finance_campaign_ee?"
Ordinarily we might answer, "How the hell should I know?" but instead assume we somehow already have access to the finance_campaign_ee function. We can call it any way we wish and get extra information. Using this extra information, could we answer the question?

"Well sure," you would say, all you have to do is call 

finance_campaign_ee( 100, [PA, VA, MI, MA, NY])

and see if PA is in the list. 

Fine. Now let's change the game. Suppose we have access to finance_campaign_ee but it is slightly broken. It only works if the list of states is of length 4 or less. In other words, can we answer the question "Is PA in finance_campaign_ee(100, [PA, VA, MI, MA, NY])?"
by using information we can gather from calls to finance_campaign_ee(num, other_states)
where other_states must contain fewer elements than [PA, VA, MI, MA, NY]?

This is a common theme which recurs in problems solved by recursion. You break a problem down into similar but smaller problems. In this case the similarity comes from describing the output of finance_campaign_ee in terms of the output of other calls to finance_campaign_ee. The "smaller problem" aspect comes from requiring that other_states must be smaller than [PA, VA, MI, MA, NY]. We need to demand that finance_campaign_ee be "slightly broken" so that it force us to solve the big problem in terms of smaller problems. That's an important part of how recursion manages to solve problems.

Think about how you would solve the above puzzle for 30 minutes. If you solve the puzzle, you will have essentially know the solution to the problem. If you don't solve it in 30 minutes, read on and don't worry about it -- solving these problems is largely a matter of having seen a similar problem solved before. 

[*]You can answer the question above in terms of other answers you can get using finance_campaign_ee:

You have 100 dollars. There are two cases to consider. You could invest 15 dollars campaigning in PA (Case I), or you could ignore PA (Case II).

Case I: If you choose to campaign in PA, then the relevant question is "What is the maximum number of votes I can win with the 85 dollars remaining?" The answer is 

votes_with_PA=total_evotes(finance_campaign_ee( 85, [VA, MI, MA, NY]) )+15

Case II: If you ignore PA, then the relevant question is "What is the maximum number of votes I can win by campaigning in some subset of [VA, MI, MA, NY] with 100 dollars?" The answer is 

votes_without_PA=total_evotes(finance_campaign_ee( 100, [VA, MI, MA, NY]) )

The two formulas above, when evaluated, are numbers. They represent the maximum number of votes you can attain if you campaign in PA, or if you don't campaign in PA.

You can decide which Case is better by comparing the two numbers.

[*]Now ask yourself, how can I add code to finance_campaign_ee to make this decision-making happen? And if I do, will finance_campaign_ee have the magic black-box property?

[/list]

---

### Post by luke77 on 2008-09-29
unutbu, just to let you know...I saw your latest response, read through the first half, and decided to wait a few days and come back to the problem before reading on. Thanks again for the response and I may have more in a day or two.

---

### Post by luke77 on 2008-10-04
Ok, I give up. Can anyone tell me how to solve this?

---

### Post by luke77 on 2008-10-05
Anyone?

---

### Post by unutbu on 2008-10-05
[PHP]def finance_campaign_ee(budget, free_states): 
    """
    Takes a budget, in dollars, and a list of available states, as a
    list of dictionaries.

    Computes and returns the list of states that maximizes the total
    number of electoral votes such that these states can be acquired
    on the budget. Returns an empty list if no states can be acquired.
    """
    cheap_states=[]
    for s in free_states:
        if s['pop'] <= budget:
            cheap_states.append(s)

    # Base case
    if len(cheap_states)==0:
        res_list=[]
    # Recursive case
    else:
        curr_state=cheap_states[0]
        other_states=cheap_states[1:]

        inc_states=finance_campaign_ee( budget-curr_state['pop'],
                                        other_states)
        inc_states.append(curr_state)
        inc_evotes=total_evotes(inc_states)

        excl_states=finance_campaign_ee( budget, other_states )
        excl_evotes=total_evotes(excl_states)

        # ... your code goes here ...
        if inc_evotes > excl_evotes:
            res_list=inc_states
        else:
            res_list=excl_states
            
    return res_list
[/PHP]

---

### Post by 10:18_pressReturn on 2009-05-15
It was inevitable. I'm currently doing the same thing as luke77, but my problem comes with the branch and bound section of this problem.

I understand the recursion and what the exhaustive enumeration is doing here, but I'm at a complete loss as to the branch and bound approach. It's a shame this course didn't provide any access to lectures; that could have been helpful.

From what I've gleaned from the last few days of internet research, I've come to realize that this is basically just an 0-1 knapsack problem where the values are electoral votes and the weights are populations. I can't seem to wrap my head around what a branch and bound solution should look like in python, though. The implication is that this shouldn't be too daunting a problem, since the tools presented up to this point don't facilitate more advanced methods, but I still can't figure it out.

Of course, being that there hasn't been activity here since October '08, I may be making an inquiry to a dead thread, but if there's anyone listening, any help would be appreciated.

---

### Post by unutbu on 2009-05-16
I'd be very happy if others would look at this and contribute more knowledge or a better algorithm. 

I have no good idea how to improve the branching, so the branching is done the same way as finance_campaign_ee did it.

The key to bounding it seems, is to estimate the maximum evotes possible under each branch, and ignoring a branch if the best it can do is not good enough. 

There are many ways to make such an estimation, and that is what makes this problem fun.
I've included below a rather simple bounding estimation. I've tried more complicated things, but this seems to work as well as anything I've tried.

I'd love to see if anyone can do better. I'm confident it is possible.

[PHP]
#!/usr/bin/env python
from __future__ import division
from time import time

# --- a list(tuple) of states ---
# each state is represented by a dictionary
# key 'name' contains the name of the state
# key 'pop' contains the total population of the state
# key 'evotes' contains the number of electoral votes 

state_list=(
    {'evotes':3, 'name':'Wyoming', 'pop':515004},
    {'evotes':21, 'name':'Pennsylvania', 'pop':12440621},   
    {'evotes':6, 'name':'Arkansas', 'pop':2810872},
    {'evotes':13, 'name':'Virginia', 'pop':7642884},
    {'evotes':31, 'name': 'New York', 'pop': 19306183},
    {'evotes':3, 'name':'South Dakota', 'pop':781919},
    {'evotes':7, 'name':'Iowa', 'pop':2982085},
    {'evotes':10, 'name':'Minnesota', 'pop':5167101},
    {'evotes':17, 'name':'Michigan', 'pop':10095643},
    {'evotes':34, 'name':'Texas', 'pop':23507783},
    {'evotes':15, 'name':'New Jersey', 'pop':8724560},
    {'evotes':11, 'name':'Washington', 'pop':6395798},
    {'evotes':4, 'name':'Hawaii', 'pop':1285498},
    {'evotes':6, 'name':'Kansas', 'pop':2764075},
    {'evotes':55, 'name': 'California', 'pop': 36457549},
    {'evotes':5, 'name':'Nevada', 'pop':2495529},
    {'evotes':21, 'name':'Illinois', 'pop':12831970},
    {'evotes':7, 'name':'Connecticut', 'pop':3504809},
    {'evotes':15, 'name':'Georgia', 'pop':9363941},
    {'evotes':7, 'name':'Oregon', 'pop':3700758},
    {'evotes':5, 'name':'Utah', 'pop':2550063},
    {'evotes':11, 'name':'Indiana', 'pop':6313520},
    {'evotes':10, 'name':'Wisconsin', 'pop':5556506},
    {'evotes':10, 'name':'Maryland', 'pop':5615727},
    {'evotes':27, 'name': 'Florida', 'pop': 18089888},
)

# Problem 1: Utility functions
# A)
def total_pop(states):
    """
    Takes a list of dictionaries of states as a parameter. Computes
    and returns the total population as an integer.
    """
    return sum([state['pop'] for state in states])

# B)
def total_evotes(states):
    """
    Takes a list of dictionaries of states as a parameter. Computes
    and returns the total number of electoral votes as an integer.
    """
    return sum([state['evotes'] for state in states])

# C)
def cheapest_evotes(states):
    """
    Takes a list of dictionaries of states as a parameter. Finds and
    returns the dictionary corresponding to the state with smallest
    population per electoral vote.
    """
    tmp=list(states)
    tmp.sort(key=lambda state: state['pop']/state['evotes'])
    return tmp[0]

def min_max_epp(states):
    """
    Takes a list of dictionaries of states as a parameter. Returns
    the min and max ratio of electoral vote per population (EPP).
    """
    if len(states)==0:
        return (0,0)
    elif len(states)==1:
        state=states[0]
        epp=state['evotes']/state['pop']
        return (epp,epp)
    else:
        tmp=[state['evotes']/state['pop'] for state in states]
        tmp.sort()
        return (tmp[0],tmp[-1])

# Problem 2: Exhaustive enumeration
def finance_campaign_ee(budget, free_states): 
    """
    Takes a budget, in dollars, and a list of available states, as a
    list of dictionaries.

    Computes and returns the list of states that maximizes the total
    number of electoral votes such that these states can be acquired
    on the budget. Returns an empty list if no states can be acquired.
    """
    cheap_states=[]
    for s in free_states:
        if s['pop'] <= budget:
            cheap_states.append(s)

    # Base case
    if len(cheap_states)==0:
        res_list=[]
    # Recursive case
    else:
        curr_state=cheap_states[0]
        other_states=cheap_states[1:]

        inc_states=finance_campaign_ee( budget-curr_state['pop'],
                                         other_states)
        inc_states.append(curr_state)
        inc_evotes=total_evotes(inc_states)

        excl_states=finance_campaign_ee( budget, other_states )
        excl_evotes=total_evotes(excl_states)
        if inc_evotes>excl_evotes:
            res_list=inc_states
        else:
            res_list=excl_states
    return res_list

def print_finance_campaign(budget, free_states, method='bb'):
    """
    Pretty-prints the output of finance_campaign_ee() and (TODO)
    prints the amount of time it took to do the computation.
    """
    t1=time()
    if method=='ee':
        states = finance_campaign_ee(budget, free_states)
    else:
        states = finance_campaign_bb(budget, free_states)
    t2=time()
    print "States where to run the campaign:"
    if len(states) == 0:
        print " No satisfactory solutions found",
    else:
        print ", ".join([s['name'] for s in states])
    print "Total number of electoral votes acquired:", total_evotes(states)
    print "Total budget required:", total_pop(states)
    print('Execution time: %s seconds'%(t2-t1))

# Problem 3: Branch and bound
def finance_campaign_bb_recurse(budget, free_states):
    '''
    The branching is exactly the same as that done by finance_campaign_ee.
    We pick off the first cheap_state and ask should this state be included in the
    result list or not?

    inc_states is the best we can do while including curr_state.
    inc_evotes is the total number of evotes achieved by inc_states
    If inc_evotes is bigger than the total number of evotes possible by all other_states,
    then inc_states is better than excl_states since excl_states is a subset of 
    other_states.
    '''
    cheap_states=[]
    for s in free_states:
        if s['pop'] <= budget:
            cheap_states.append(s)
    # Base case
    if len(cheap_states)==0:
        res_list=[]
    # Recursive case
    else:
        curr_state=cheap_states[0]
        other_states=cheap_states[1:]
        inc_states=finance_campaign_bb_recurse(budget-curr_state['pop'],other_states)
        inc_states.append(curr_state)
        inc_evotes=total_evotes(inc_states)
        if inc_evotes>total_evotes(other_states):
            # Here we take advantage of the bound
            res_list=inc_states
        else:
            excl_states=finance_campaign_bb_recurse(budget,other_states)
            excl_evotes=total_evotes(excl_states)
            if inc_evotes>excl_evotes:
                res_list=inc_states
            else:
                res_list=excl_states
    return res_list


def finance_campaign_bb(budget, free_states):
    """
    Takes a budget, in dollars, and a list of available states, as a
    list of dictionaries.

    Computes and returns the list of states that maximizes the total
    number of electoral votes such that these states can be acquired
    on the budget. Returns an empty list if no states can be acquired.
    """
    tmp=list(free_states)
    tmp.sort(key=lambda state: state['pop'],reverse=True)
#     It is helpful to sort the states in descending order by 'pop' or 'evotes'.
#     finance_campaign_bb_recurse has two arguments: budget and free_states.
#     Reducing either of these as quickly as possible helps
#     finance_campaign_bb_recurse finish faster. Therefore, we want either the
#     budget to be reduced quickly, or the number of free_states to be reduced
#     quickly. By sorting in descending order by 'pop', we reduce the budget more
#     quickly.
    return finance_campaign_bb_recurse(budget,tmp)

if __name__=='__main__':
    budget=90000000
    the_list=state_list
#     the_list=state_list[:30]
    print_finance_campaign(budget,the_list,method='bb')
#     print
#     print_finance_campaign(budget,the_list,method='ee')
[/PHP]

Result:
```

% ps5.py
States where to run the campaign:
Wyoming, South Dakota, Hawaii, Nevada, Utah, Kansas, Arkansas, Iowa, Connecticut, Oregon, Minnesota, Wisconsin, Indiana, Washington, Virginia, Michigan, Pennsylvania, Illinois
Total number of electoral votes acquired: 167
Total budget required: 89834655
Execution time: 5.83373212814 seconds
```

PS. Everything I know abound branch and bound -- which is to say, very little -- I learned here:
[http://en.wikipedia.org/wiki/Branch_and_bound](http://en.wikipedia.org/wiki/Branch_and_bound)

---

### Post by 10:18_pressReturn on 2009-05-16
Wow. I was right there and didn't realize it. All the ideas were in place including the bound; It was the proper usage of the bound that was elusive. I kept convincing myself that I was on my way to restating the ee method. Thanks for the enlightenment.

The only part I'm a bit fuzzy on is the 'key' argument for the list method sort(). What's its general purpose? Like, say you used it on a list of integers instead of dictionaries. What would you set it to and what would be its effect? Additionally, in this particular case, why did you set it to a lambda (I guess I'm still a greenhorn programmer who's wrestling with the value of lambda as a programming construct) instead of just the value that lambda calculates/returns?

---

### Post by unutbu on 2009-05-16
This is where I learned how to sort in Python: [http://wiki.python.org/moin/HowTo/Sorting](http://wiki.python.org/moin/HowTo/Sorting). It's a good read, well worth studying.

Sometimes when you have a non-numerical list and want to sort the list according to some characteristic, the "list.sort(key=func)" idiom is useful.

Each element of list is sent to func.
It is func's job to return a number or, more generally, something which is orderable.

In this case, each element of tmp is a state -- a dictionary.
I wanted to sort by the dictionary's 'pop' key, so func has to take a state and return the value associated with the 'pop' key.

(lambda state: state['pop']) does that.

If you had a list of integers, you usually don't need the "list.sort(key=func)" idiom. Here is a contrived example however: Suppose you have a function 

def num_factors(num)  --> Returns the number of factors of integer num

Then you could sort a list of integers according to the number of factors with
```

list.sort(key=num_factors)

list=[1,2,3,4,5,6,7,8]
list.sort(key=num_factors)
```
list would now equal [1,2,3,5,7,4,6,8].

---

### Post by 10:18_pressReturn on 2009-05-17
Okay.  That all makes good sense.  I appreciate the help.

---

