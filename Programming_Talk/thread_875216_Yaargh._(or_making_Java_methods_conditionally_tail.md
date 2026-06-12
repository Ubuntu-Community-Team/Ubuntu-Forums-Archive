---
title: "Yaargh. (or making Java methods conditionally tail recurse [if that's the problem..])"
date: 2008-07-30
forum: Programming Talk
---

### Post by Chake99 on 2008-07-30
I was trying to answer this programming exercise [here](http://www.cemc.uwaterloo.ca/ccc/2005/senior/pinball2.pdf)

(In brief, given a list of scores that are in chronological order, find the average rank of all the scores at the time when they were input [e.g. the rank of any given score is found only by regarding those that came before it].)

And I wrote this program:

[spoiler]
```

import java.io.*;

class PinballGame {

	static int rankTotal = 1;
	static int numRanks;
	static int curRank;

	public static void main (String[] args) throws IOException {

		FileReader reader = new FileReader("PinballGame.in");
		BufferedReader br = new BufferedReader(reader);
		TreeNode topNode;
		double tmp;
		double avg;

		numRanks = Integer.parseInt(br.readLine());
		topNode = new TreeNode(1, Integer.parseInt(br.readLine()));
		
		for(int i = 1; i < numRanks; i++) {
			curRank = 1;
			insert(topNode, Integer.parseInt(br.readLine()));	
		}

		tmp = ((double)rankTotal)/numRanks * 100;
		avg = Math.round(tmp);
		avg /= 100.0;

		System.out.println(avg);
	}

	public static void insert(TreeNode curNode, int score) {
		if (curNode.dummy) {
			curNode.dummy = false;
			curNode.leftNode = new TreeNode();
			curNode.rightNode = new TreeNode();
			curNode.rank = curRank;
			curNode.score = score;

			//System.out.println(curRank);
			rankTotal += curRank;
		} else {
			if (score >= curNode.score) {
				curNode.rightTree++;
				insert(curNode.rightNode, score);
			} else {
				curRank += curNode.rightTree + 1;
				curNode.leftTree++;
				insert(curNode.leftNode, score);
			}
		}
	}
}

class TreeNode {

	public TreeNode leftNode, rightNode;
		
	public int rank, score, leftTree, rightTree;
	public boolean dummy;		

	TreeNode() {
		rank = 0;
		score = 0;
		leftTree = 0;
		rightTree = 0;
		leftNode = null;
		rightNode = null;
		dummy = true;
	}
	TreeNode (int rank, int score) {
		this.rank = rank;
		this.score = score;
		leftTree = 0;
		rightTree = 0;
		leftNode = new TreeNode();
		rightNode = new TreeNode();
		dummy = false;
	}
}


```
[/spoiler]

(Yes, I know its a godawful mess but I was trying to write it quickly, question is from a timed competition)

It works for answers where the number of rankings that must be found aren't huge. However it terminates with an error (don't know which one, console is filled with messages saying which line is the problem, which are either of the lines calling insert recursively) if I try some of the much larger datasets, e.g. 9 and 10 from here:

[http://access.mmhs.ca/ccc/](http://access.mmhs.ca/ccc/)

(under 2005 pinball, midway down).

I'm pretty sure changing the insertion recurse to a while loop to find the appropriate parent node could solve the problem, but I'd like to know if there's a way to make this not grow on the stack (if that's indeed the problem) while working recursively.

Thanks in advance.

(edit: I had an else if < following an if >= . >.< . )

---

### Post by Zugzwang on 2008-07-31
Consider using a debugger to execute your program step-by-step. We won't solve your homework here, but for infinite recursion, this is usually a good approach. :-)

---

