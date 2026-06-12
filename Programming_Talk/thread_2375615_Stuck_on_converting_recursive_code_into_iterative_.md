---
title: "Stuck on converting recursive code into iterative code that uses a Stack (in Java)"
date: 2017-10-26
forum: Programming Talk
---

### Post by s3a on 2017-10-26
Hello, everyone.

I'm stuck on converting recursive code into iterative code that uses a Stack, but, even after days of "breaking my head," I still haven't figured it out. :(

I had an assignment question ( [https://www.docdroid.net/YOP9dkK/stuckonprogrammingquestion.pdf#page=3](https://www.docdroid.net/YOP9dkK/stuckonprogrammingquestion.pdf#page=3) ) for which I needed to be able to do this, but I was, unfortunately, not able to figure this out on time for that assignment's deadline, and that will likely cost me a lot of marks, but there's nothing I can do about that anymore, and I have a test coming up soon, and that topic may come up again (but, even if it doesn't, I would still really like to know), so I would really appreciate it if someone could help me figure it out as soon as possible, because I have so much material to learn in a short amount of time that I feel overwhelmed.

Here's my (Java) code.:
[http://dpaste.com/1TSCAGT](http://dpaste.com/1TSCAGT)

[http://dpaste.com/2XQ8C9B](http://dpaste.com/2XQ8C9B)

Basically, my question is how do I make *public boolean iterativeVersion(int index, int[] theRow, boolean[] visited)* do what *public boolean recursiveVersion(int index, int[] theRow, boolean[] visited)* does?

Any input would be greatly appreciated!

P.S.
If you need more information, just let me know.

---

### Post by trent.josephsen on 2017-10-29
This is an interesting problem. Of course, any recursive algorithm *can* be transformed into an iterative algorithm with a stack -- after all, that's how recursion is implemented on real hardware! But actually performing the transformation often requires explicit attention to all the pieces of state that are implicitly stored on the stack when you do a function call. In effect, you have to use the stack to emulate function calls, without using any actual function calls.

Before I dive into implementation, though, let me warn you: there's at least one simpler algorithm that does *not* use a stack (but does use a different growable data structure). I will let you figure that out on your own if you want to.

So, let's look at the recursive algorithm (in pseudocode):

```
Let the function recursiveVersion(index, theRow, visited) have this behavior:

    If theRow[index] is 0,
        stop and **return** True. (The game is solved.)

    If visited[index] is True,
        stop and **return** False. (We already tried to solve the game by starting here; the solution will not visit it again.)

    Set visited[index] to True.

    Calculate rightIndex to be (index + theRow[index]/2) (ignore the rounding issues for now).
    If rightIndex is within theRow,
        **call** recursiveVersion(rightIndex, theRow, visited)
        and if the result is True, stop and **return** True.

    Calculate leftIndex to be (index - theRow[index]/2).
    If leftIndex is within theRow,
        **call** recursiveVersion(leftIndex, theRow, visited)
        and if the result is True, stop and **return** True.

    At this point, if we haven't found a solution through leftIndex or rightIndex,
        stop and **return** False. (The game is not solvable by starting at index.)
```

The subroutine **call**s are what make an iterative transformation tricky. What does a subroutine call do?
[LIST=1]
[*]Saves the **return address** (the program counter, or continuation register) on the stack.
[*]Saves (pushes) the values of local variables on the stack.
[*]Sets the local parameters of the called function to be the values of the arguments passed to it.
[/LIST]

And when you **return** from a subroutine, it reverses those steps:
[LIST=1]
[*]Restores (pops) the values of local variables from the stack, to what they were before the call (discarding the local variables of the callee).
[*]Jumps back to the return address to continue where the caller left off.
[/LIST]

It's the return address, aka the continuation, that is implicit in the recursive solution and absent in your StackFrame class. StackFrame currently stores no knowledge about *where it should return to*; therefore, you can't continue where you left off -- you don't know whether to continue after the first **call** or after the second one.

With function calls and normal iterative code in general, continuations are implicit; you don't think about them at all. But in this case we need to "reify" that continuation just a little bit -- we need to know which place to jump back to. There are only two recursive calls, so you only need to distinguish between two possible continuations -- you could use a Boolean for that. So suppose we add a bool to StackFrame that is False for the first call and True for the second one -- now we know what to do. Let's try it in pseudocode again. Java doesn't have labels or a goto construct, but it's really easier to write this kind of code with them, so I won't let that bother me.

```
Let iterativeVersion(index, theRow, visited) be a function with this implementation:

    Create an empty stack.

LOOP_START:
    If theRow[index] is 0, stop and return True (breaking out of the loop).

    If visited[index] is True, (this is where we return to the caller in the recursive version)
        try to pop a frame off the stack.
        If the stack is empty,
            stop and return False (we returned to the starting point and there are no more paths to try).
        Otherwise,
            set the values of index, theRow and visited to the values of those fields in the popped frame.
            If the frame's continuation is False, go to FIRST; but if it is True, go to SECOND.

    Set visited[index] = True.

    Let continuation = False.
    Let rightIndex = index + theRow[index]/2.
    If rightIndex is within theRow, (this is where we make a recursive call in the recursive version)
        push (index, theRow, visited, continuation) onto the stack as a new frame.
        Set index = rightIndex.
        Go back to LOOP_START.

FIRST:
    Set continuation = True.
    Let leftIndex = index - theRow[index]/2.
    If leftIndex is within theRow,
        push (index, theRow, visited, continuation) onto the stack as a new frame.
        Set index = leftIndex.
        Go back to LOOP_START.

SECOND:
    Try to pop a frame off the stack.
    If the stack is empty,
        stop and return False (we returned to the starting point and there are no more paths to try).
    Otherwise,
        set the values of index, theRow and visited to the values of those fields in the popped frame.
        Go back to LOOP_START.
```

There's another optimization you should make before transforming this into Java code, and that's to realize that theRow and visited never change. Therefore, they don't need to be pushed onto the stack and popped off multiple times. StackFrame can contain just the index and the continuation and it will work fine.

Translating into Java will be a bit obnoxious because you have to translate all these "go to LABEL"s into something "structured", probably with flags or something. One way to do it is allow the "continuation" variable to have three values (corresponding to the three labels in the pseudocode above) and a switch or if/else chain inside an infinite loop. You can do better. Other languages make this easier as well. But to be perfectly honest, it's been a long time since I wrote Java and I don't really feel like trying to pull it all together into real code. So instead, here's the Python version I wrote for the sake of confirming this approach would work:

```
LOOP_START = 'LOOP_START'
FIRST = 'FIRST'
SECOND = 'SECOND'

def iterative_solve(index, row):
    stack = []
    visited = [False for _ in row]
    continuation = LOOP_START

    while True:
        if continuation is LOOP_START:
            if row[index] == 0:
                return True

            if visited[index]:
                if len(stack) == 0:
                    return False
                else:
                    index, continuation = stack.pop()
                    continue

            visited[index] = True

            continuation = FIRST
            right_index = index + (row[index] + 1)//2
            if right_index in range(len(row)):
                stack.append((index, continuation))
                index, continuation = right_index, LOOP_START
        elif continuation is FIRST:
            continuation = SECOND
            left_index = index - (row[index] + 1)//2
            if left_index in range(len(row)):
                stack.append((index, continuation))
                index, continuation = left_index, LOOP_START
        elif continuation is SECOND:
            continuation = LOOP_START
            if len(stack) == 0:
                return False
            else:
                index, continuation = stack.pop()
        else:
            print("something has gone horribly wrong")

```

I don't know how well you understand Python, but if not well enough, hopefully the pseudocode will help.

If this kind of thing interests you, or even if it doesn't, I would recommend getting a copy of *Structure and Interpretation of Computer Programs*, which deals with many ways of representing procedures, some of which may make the transformation from recursive to iterative more obvious. You can also [read it online](https://mitpress.mit.edu/sicp/).

Good luck!

---

