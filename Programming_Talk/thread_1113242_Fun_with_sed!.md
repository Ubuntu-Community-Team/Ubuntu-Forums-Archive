---
title: "Fun with sed!"
date: 2009-04-01
forum: Programming Talk
---

### Post by MaxIBoy on 2009-04-01
So, yesterday morning, I decided to write a small program entirely in sed. It was actually easier than I thought it would be. Here's what I've come up with:

```
#! /bin/sed -nuf


x
/%/!{
s/^.*$/@1%1x\n.-----.\n| | | ]\n-------\n| | | ]\n-------\n| | | ]\n'-----'\nMake yRur neLT mRve.../
i\
current position 1, 1\
next move goes to player "x"\
.-----.\
| | | ]\
-------\
| | | ]\
-------\
| | | ]\
'-----'\
Make the first move...\
\
\

x
d
}
x

/_/!{
s/^.*$/&_/g
s/./&\n/g
}
/_/ {
/^s/{
x
s/%1/%2/g
s/%0/%1/g
x
}
/^a/{/|O|O|O/{ i O wins! 
s/^.*$//; x; d }
x
s/@1/@0/g
s/@2/@1/g
x
}
/^w/{
x
s/%1/%0/g
s/%2/%1/g
x
}
/^d/{
x
s/@1/@2/g
s/@0/@1/g
x
}
/^_/{
x
/x/{
/@0%0/ s/|./&QX/1
/@1%0/ s/|./&QX/2
/@2%0/ s/|./&QX/3
/@0%1/ s/|./&QX/4
/@1%1/ s/|./&QX/5
/@2%1/ s/|./&QX/6
/@0%2/ s/|./&QX/7
/@1%2/ s/|./&QX/8
/@2%2/ s/|./&QX/9
/| QX/!{ 
s/x/t/
i Spot already taken, sorry
}
s/|OQX/|O/g
s/| QX/|X/g
s/|XQX/|X/g
}
/o/{
/@0%0/ s/|./&QO/1
/@1%0/ s/|./&QO/2
/@2%0/ s/|./&QO/3
/@0%1/ s/|./&QO/4
/@1%1/ s/|./&QO/5
/@2%1/ s/|./&QO/6
/@0%2/ s/|./&QO/7
/@1%2/ s/|./&QO/8
/@2%2/ s/|./&QO/9
/| QO/!{ 
s/o/x/
i Spot already taken, sorry
}
s/|XQO/|X/g
s/| QO/|O/g
s/|OQO/|O/g
}
s/t/x/
s/x/_/
s/o/x/
s/_/o/
h

/|O|O|O]/{ i O wins! 
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d }
/|O|.|.].*|O|.|.].*|O|.|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|O|.].*|.|O|.].*|.|O|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|O].*|.|.|O].*|.|.|O]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|O|.|.].*|.|O|.].*|.|.|O]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|O].*|.|O|.].*|O|.|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|X|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|.|.].*|X|.|.].*|X|.|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|X|.].*|.|X|.].*|.|X|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|X].*|.|.|X].*|.|.|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|.|.].*|.|X|.].*|.|.|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|X].*|.|X|.].*|X|.|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/| /!{ i No more possible moves!
s/M.*\.//; s/@.%..//g; p; s/^.*$//; x; d; }


s/T/t/
s/R/o/g
s/@/current p_siti_n /
s/%/, /
s/[xo]/\nnext m_ve g_es t_ player "&"/
s/L/x/g
s/_/o/g
p
i\
\

d
}
D
}


```

It's a two-player tic-tac-toe game. The controls are WASD, and in the command-prompt style. So, to move the cursor from the upper-left to the lower right, you'd type ssdd[ENTER] or sdsd[ENTER.] Once you've made your move, pass the keyboard over to your opponent, because I haven't made an AI yet. Features automatic victory detection. The draw detection is a little lacking; it simply calls a draw if no one's won and there are no empty slots.


Has anyone else done anything similar to this with sed?

---

### Post by WitchCraft on 2009-04-01
> **MaxIBoy said:**
> So, yesterday morning, I decided to write a small program entirely in sed. It was actually easier than I thought it would be. Here's what I've come up with:

```
#! /bin/sed -nuf


x
/%/!{
s/^.*$/@1%1x\n.-----.\n| | | ]\n-------\n| | | ]\n-------\n| | | ]\n'-----'\nMake yRur neLT mRve.../
i\
current position 1, 1\
next move goes to player "x"\
.-----.\
| | | ]\
-------\
| | | ]\
-------\
| | | ]\
'-----'\
Make the first move...\
\
\

x
d
}
x

/_/!{
s/^.*$/&_/g
s/./&\n/g
}
/_/ {
/^s/{
x
s/%1/%2/g
s/%0/%1/g
x
}
/^a/{/|O|O|O/{ i O wins! 
s/^.*$//; x; d }
x
s/@1/@0/g
s/@2/@1/g
x
}
/^w/{
x
s/%1/%0/g
s/%2/%1/g
x
}
/^d/{
x
s/@1/@2/g
s/@0/@1/g
x
}
/^_/{
x
/x/{
/@0%0/ s/|./&QX/1
/@1%0/ s/|./&QX/2
/@2%0/ s/|./&QX/3
/@0%1/ s/|./&QX/4
/@1%1/ s/|./&QX/5
/@2%1/ s/|./&QX/6
/@0%2/ s/|./&QX/7
/@1%2/ s/|./&QX/8
/@2%2/ s/|./&QX/9
/| QX/!{ 
s/x/t/
i Spot already taken, sorry
}
s/|OQX/|O/g
s/| QX/|X/g
s/|XQX/|X/g
}
/o/{
/@0%0/ s/|./&QO/1
/@1%0/ s/|./&QO/2
/@2%0/ s/|./&QO/3
/@0%1/ s/|./&QO/4
/@1%1/ s/|./&QO/5
/@2%1/ s/|./&QO/6
/@0%2/ s/|./&QO/7
/@1%2/ s/|./&QO/8
/@2%2/ s/|./&QO/9
/| QO/!{ 
s/o/x/
i Spot already taken, sorry
}
s/|XQO/|X/g
s/| QO/|O/g
s/|OQO/|O/g
}
s/t/x/
s/x/_/
s/o/x/
s/_/o/
h

/|O|O|O]/{ i O wins! 
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d }
/|O|.|.].*|O|.|.].*|O|.|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|O|.].*|.|O|.].*|.|O|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|O].*|.|.|O].*|.|.|O]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|O|.|.].*|.|O|.].*|.|.|O]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|O].*|.|O|.].*|O|.|.]/{ i O wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|X|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|.|.].*|X|.|.].*|X|.|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|X|.].*|.|X|.].*|.|X|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|X].*|.|.|X].*|.|.|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|X|.|.].*|.|X|.].*|.|.|X]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/|.|.|X].*|.|X|.].*|X|.|.]/{ i X wins!
s/M.*\.//;s/@.%..//g; p; s/^.*$//; x; d; }
/| /!{ i No more possible moves!
s/M.*\.//; s/@.%..//g; p; s/^.*$//; x; d; }


s/T/t/
s/R/o/g
s/@/current p_siti_n /
s/%/, /
s/[xo]/\nnext m_ve g_es t_ player "&"/
s/L/x/g
s/_/o/g
p
i\
\

d
}
D
}


```It's a two-player tic-tac-toe game. The controls are WASD, and in the command-prompt style. So, to move the cursor from the upper-left to the lower right, you'd type ssdd[ENTER] or sdsd[ENTER.] Once you've made your move, pass the keyboard over to your opponent, because I haven't made an AI yet. Features automatic victory detection. The draw detection is a little lacking; it simply calls a draw if no one's won and there are no empty slots.


Has anyone else done anything similar to this with sed?

Not a game, but 99 bottles of beer :lolflag:

---

