---
title: "Programming Challenge 14: Mastermind"
date: 2008-06-09
forum: Programming Talk
---

### Post by matja on 2008-06-09
This programming challenge is to create a [Mastermind]("http://en.wikipedia.org/wiki/Mastermind_(board_game)") solver. Given an input file with codes separated by new lines
```

ACEA
FECC
BAFC

```
the program should print the number of guesses it had to make before finding the correct sequence, also separated by new lines.
```

9
5
7

```
The six different possible colors are represented by the characters A-F in upper case.

You will also have to write the routine that given a guess returns the hints, e.g. a red flag for every right color in the right place and a white flag for every right color in the wrong place (see the wikipedia [ref.]("http://en.wikipedia.org/wiki/Mastermind_(board_game)")). Try to clearly divide your program in one "codemaker" and one "codebreaker" part, where the codebreaker calls routines in the codemaker part but not vice versa. I realize that the possibilities for cheating are endless, but I can trust you, right? ;)

My intention is to feed each entry with a large input file (not revealed here) of codes and determine the mean number of guesses needed. A low mean will of course be an advantage for your contribution, although other factors may also weigh in.

The above description is the minimum requirements of a contribution.

Some suggestions of improvements are:
[LIST]
[*]Let the program print each guess it makes and the codemakers hints, to make it look more like the real game.
[*]Make this more graphical, i.e. use colors instead of the letters A-F.
[*]Make it a real Mastermind game, i.e. let the user make the guesses.
[/LIST]
With any of the above suggestions or your own, which are most welcome by the way, there must exist an option to just print the number of guesses needed as stated by the minimum requirements above.

If I've forgotten to add something, just ask. The deadline is set to next monday, the 16th of June, at 15:00 GMT. Good luck!

---

### Post by stevescripts on 2008-06-10
Interesting ...

and more challenging than I originally thought.

Steve

---

### Post by MacUntu on 2008-06-12
Afaik there is a proven fastest (avg) strategy, right?

Edit:

Kenji Koyama and Tony W. Lai: 4.340 expected moves, one worst case with 6 moves.
Donald E. Knuth: 4.341 expected moves, worst case 5 moves.

---

### Post by matja on 2008-06-12
> **MacUntu said:**
> Afaik there is a proven fastest (avg) strategy, right?

Edit:

Kenji Koyama and Tony W. Lai: 4.340 expected moves, one worst case with 6 moves.
Donald E. Knuth: 4.341 expected moves, worst case 5 moves.

I couldn't find the references in the *Journal of Recreational Mathematics*, so I don't know if they've been proven to be the fastest. If not, I expect we'll have found the fastest by monday ;)

How's it going with this, I hope it wasn't too hard? The entries aren't overwhelming in numbers so far! Maybe some free time this weekend will do wonders...

---

### Post by red_Marvin on 2008-06-12
I'm working on one in python, the generator/breaker is finished and seems to work well, but I have yet to make it conform to the strict I/O standards of the challenge, and to comment the code.

---

### Post by MacUntu on 2008-06-13
IIRC they started a brute force attack on every possible strategy - that's how they found the best one.

I'd code it but I'm outta time, sorry.

---

### Post by red_Marvin on 2008-06-14
Here's my submission so far, with a filename supplied on the command line it runs as per the benchmark specifications, with no cli parameters it runs a simple text game.

I've commented the code and written doc strings, but if extra explanation is needed, please ask.


```
import random

class codemaker:
	"""Creates codes and evaluates input"""

	def __init__(self, codelength, numberrange, forcedcode = None):
		"""codelength:		length of the code
		numberrange:		range of each number of the code
		forcedcode:		supply a code here to force the instance to
		                        use it instead of creating a random one"""

			# variable initializations
		self.rng = random.Random()
		self.cl = codelength
		self.dr = numberrange

			# create a code or use the one supplied	
		if forcedcode:
			self.code = forcedcode
		else:
			self.code = []
			self.code = [self.rng.randint(0, self.dr-1) for i in range(self.cl)]


	def evaluate(self, suggestion):
		"""Evaluates a code suggestion and returns a score tuple
		(number of right numbers on right place, number of right numbers on wrong place)"""

			# keep indexes that have already been resulted in a scorepoint
		takensu = []
		takenso = []

			# check for right colours in the right place
		rcrp = 0
		for i in range(self.cl):
			if suggestion[i] == self.code[i]:
				rcrp += 1
				takensu.append(i)
				takenso.append(i)

			# check for right colours in the wrong place
		rcwp = 0
		for i in range(self.cl):
				for j in range(self.cl):
					if i not in takensu and j not in takenso:
						if suggestion[i] == self.code[j]:
							rcwp += 1
							takensu.append(i)
							takenso.append(j)
		return rcrp, rcwp


	def reveal(self):
		"""Just returns the code"""

		return self.code



class codebreaker:
	"""Breaks codes"""

	def __init__(self, codelength, numberrange, history = None):
		"""codelength:		length of the code
		numberrange:		range of each number of the code
		history			supply a tuple consisting of
					(list of already tried combinations, list of scores those tries got)
					to solve a game that has been partially solved"""

			# variable initializations
		self.rng = random.Random()
		self.cl = codelength
		self.dr = numberrange
		self.score = (self.cl, 0)

			# generate list of all possible codes
		self.possible_combinations = generate_all_combinations(codelength, numberrange)

			# if there is a history, use it to remove impossible combinations
		if history:
			for triedcombination, reportedscore in history:
				self.sieve(triedcombination, reportedscore)


	def bruteforce_step(self):
		"""Returns code suggestions, use in combination with report() to solve a game in steps
		example:
		maker = codemaker(l, r)
		breaker = codebreaker(l, r)
		for suggestion in breaker.bruteforce_step():
			score = maker.evaluate(suggestion)
			print "[%s] => (%s)"%(" ".join([str(s) for s in suggestion]), ",".join([str(s) for s in score]))
			breaker.report(score)
		print "The last suggestion (IE the one that solved the game = the hidden one) was: [%s]"%(" ".join([str(s) for s insuggestion]))"""

		while True:
				# select and yield a suggestion
			suggestion = self.rng.choice(self.possible_combinations)
			yield suggestion
			if self.score:
					# make deductions unless we've won
				if tuple(self.score) == (self.cl, 0):
					return
				else:
					self.sieve(suggestion, self.score)



	def report(self, score):
		"""Report what score a suggestion got, see bruteforce_step()"""

		self.score = score


	def sieve(self, suggestion, score):
		"""Make deductions based on what score a code suggestion got
		(IE remove all codes that would not get the same score from the internal
		list of possible codes)"""

			# for this, for each code in the list, we create a forced maker to evaluate
			# the suggestion. If the returned score isn't the same as the one the
			# "real" maker returned, it is not a valid solution to the game
		tmp = []
		for combination in self.possible_combinations:
			little_maker = codemaker(self.cl, self.dr, combination)
			if little_maker.evaluate(suggestion) == score:
				tmp.append(combination)
		self.possible_combinations = tmp




def generate_all_combinations(codelength, numberrange):
	"""Generate a list of all possible codes based on the selected length of the code and the range
	of its individual numbers."""

	acl = [[i] for i in range(numberrange)]
	for i in range(codelength-1):
		newacl = []
		for c in acl:
			newacl.extend([c+[j] for j in range(numberrange)])
		acl = newacl
	return acl



def benchmark(filein):
	"""running mode following the specifications here http://ubuntuforums.org/showthread.php?t=823446
	filein:		the name of the file to use as code input"""
	codelength = 4
	numberrange = 6
	translationtable = {'A':0, 'B':1, 'C':2, 'D':3, 'E':4, 'F':5}
	fd = open(filein, 'rU')


	for line in [l[:-1] for l in fd.readlines()]:

			# initialization
		code = [translationtable[l] for l in line]
		maker = codemaker(codelength, numberrange, code)
		breaker = codebreaker(codelength, numberrange)

			# bruteforcing, note that the only thing we pass to the breaker
			# that has been touched by the maker is the reported score
		ctr = 0
		for suggestion in breaker.bruteforce_step():
			ctr += 1
			score = maker.evaluate(suggestion)
			breaker.report(score)

		print ctr
	fd.close()



def cligame():
	"""A simple implementation of the game"""

	import sys

	l = "foo"
	r = "bar"

	print "|\ /|"
	print "| V |"
	print "|   | a s t e r m i n d"
	print "-----------------------"

	print "Length of the hidden code"
	while not l.isdigit() or int(l) < 2:
		l = raw_input(":")
	l = int(l)
	print "Upper bound of the range of the numbers in the code"
	print "(IE the numbers in the code will come from the set [0 1 ... what you input minus one])"
	while not r.isdigit() or int(r) < 2:
		r = raw_input(":")
	r = int(r)
	maker = codemaker(l, r)
	history = []
	finishedmsg = ""
	ctr = 0

	print "Play by inputting a space separated list of numbers you think is the code,"
	print 'or "quit" to quit or "solve" to bruteforce solve it.'
	while not finishedmsg:
		i = raw_input(":")
		if i == "quit":
			finishedmsg = "Quitter!"
		elif i == "solve":
			breaker = codebreaker(l, r, [[history] and history or None][0])
			for suggestion in breaker.bruteforce_step():
				ctr += 1
				score = maker.evaluate(suggestion)
				print "#%03d [%s] => (%s)"%(ctr, " ".join([str(s) for s in suggestion]), ",".join([str(s) for s in score]))
				breaker.report(score)
			finishedmsg = "Cheater!"
		else:
			il = i.split()
			inputisvalid = True
			if len(il) < l: inputisvalid = false
			for n in il:
				if (not n.isdigit()) or int(n) < 0 or int(n) >= r: inputisvalid = False
			if inputisvalid:
				ctr += 1
				suggestion = [int(n) for n in il]
				score = maker.evaluate(suggestion)
				print "#%03d [%s] => (%s)"%(ctr, " ".join(il), ",".join([str(s) for s in score]))
				if score == (l, 0): finishedmsg = "Congratulations! You've won!"
				history.append((suggestion, score))
			else:
				print "Play by inputting a space separated list of numbers you think is the code,"
				print 'or "quit" to quit or "solve" to bruteforce solve it.'
	print finishedmsg



if __name__ == "__main__":
	import sys
	if len(sys.argv) != 2:
		cligame()
	elif len(sys.argv) == 2:
		benchmark(sys.argv[1])

```

---

### Post by slavik on 2008-06-15
for something like this, I would guess that a breadth first tree traversial should be able to handle it.

---

### Post by matja on 2008-06-15
A nice entry, red_Marvin! I found one erroneous line in the cligame function:
```
if len(il) < r: inputisvalid = false
```
should be (I assume):
```
if len(il) < **l**: inputisvalid = **F**alse
```
Now we just need someone to challenge you!

---

### Post by red_Marvin on 2008-06-15
Thanks for the correction, I've fixed my post.
Yeah I'd like some more participants too, I don't mind winning, but doing so on walk over isn't as glorious :p.

---

### Post by matja on 2008-06-16
Well, the time is up! If anyone is working on this challenge and think they will be finished soon, please reply to this thread and I can postpone the deadline a day or two. Otherwise I will announce the winner in a couple of hours (put the champagne in the fridge while we wait, red_Marvin ;))

---

### Post by Lau_of_DK on 2008-06-16
> **matja said:**
> Well, the time is up! If anyone is working on this challenge and think they will be finished soon, please reply to this thread and I can postpone the deadline a day or two. Otherwise I will announce the winner in a couple of hours (put the champagne in the fridge while we wait, red_Marvin ;))

Matja, 

Go ahead and give the guy his prize, he's really made a solid implementation.

I've struggled all week (pathetic huh?) to do a functional solution in Clojure, but for the life of me I cant get it up to speed and produce the right results, so Im throwing in the towel :(

Congratz to the winner,
Lau

---

### Post by matja on 2008-06-16
Then I'm proud to announce **red_Marvin** as the winner on knock-out! The mean number of guesses taken to break a code was 4.6 and the maximum was 8. **Congratulations!**

I look forward to the next challenge.

Mattias

---

### Post by ZuLuuuuuu on 2008-06-17
Congratulations!

I was also trying this challenge but I couldn't solve a technical problem unfortunately and also my implementations guess number was way to high compared to red_Marvins :)

---

### Post by red_Marvin on 2008-06-17
Thanks :)
I will set up the next challenge as soon I get an idea of what it should be.

---

### Post by Lux Perpetua on 2008-06-19
> **red_Marvin said:**
> Thanks :)
I will set up the next challenge as soon I get an idea of what it should be.Congratulations! Have you decided on the new challenge yet? For what it's worth, I think the most successful challenges have been easy yet interesting, and they have allowed creativity. 

Speaking only for myself, I am very unlikely to participate in a challenge that resembles a homework assignment. It's not that I suspect the challenge of really being someone's attempt to get out of doing his or her homework; it's just that I've done enough programming assignments in my college days to avoid doing more of them. This includes challenges that are too specific. Implementing a certain functionality is fine, but if the challenge requires solving a very specific (and not obviously interesting) task, then it can probably be classified as "too specific."

That's just my humble opinion, of course.

---

### Post by red_Marvin on 2008-06-19
Exactly, the challenge should be easy enough so many can participate, but not too easy, it is a challenge after all, and the topic should be interesting enough to be fun to figure out.

---

### Post by Lau_of_DK on 2008-06-24
> **red_Marvin said:**
> Exactly, the challenge should be easy enough so many can participate, but not too easy, it is a challenge after all, and the topic should be interesting enough to be fun to figure out.

And the challenge should be posted on the forum... Wheres #15 ?


/Lau

---

### Post by red_Marvin on 2008-06-24
My apologies for the delay, The new challenge has been posted here: [http://ubuntuforums.org/showthread.php?p=5254181](http://ubuntuforums.org/showthread.php?p=5254181)

---

