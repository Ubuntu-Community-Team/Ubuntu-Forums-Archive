---
title: "c++ Help"
date: 2012-12-08
forum: Programming Talk
---

### Post by zhaoc033 on 2012-12-08
On a chess board, suppose I am at (1,1) and I want to move to (7,7). Only down and right moves are allowed.
Why is this function not right?


```
void print_out(string &ans, int row, int col){
	if (row == 7 && col == 7){
		cout << ans;
	}
	else if (row >7 || col > 7)
		return;
	
	for (int i = 1; i<=2; i++){
		if (i == 1 && row < 7 && row + col <=14){
			// ans is a collection of postions
			stringstream oss;
			oss << ans << "(" << (row + 1) << ", " << col << ")" << endl;
			ans = oss.str();
			print_out(ans, row + 1, col);
		}
		if (i == 2 && col <7 && row + col <=14){
			stringstream oss;
			oss << ans << "(" << row << ", " << col +1 << ")" << endl;
			ans = oss.str();
			print_out(ans, row, col + 1);
		}
	}
	
}
```

---

### Post by Zugzwang on 2012-12-08
Please write a complete example that compiles next time. Also, you didn't describe what input you assume for the function and what your wanted output is. So I'm guessing now: you want some path to the position (7,7) be printed, and you don't care about the fact that you overwrite "and".

Actually, your function prints out such a trace for me. The only problem is that afterwards, much more is printed. So here is a hint for you: you are using recursion, and thus in your for loop, you can first branch into the first if(...) block, and then in the next iteration of the loop, you can branch into the second if(...) block. This even holds if you are returning from a recursive call, and have already printed out a path to the goal. In a way, you are thus printing out *all* of the possible paths, which forgetting to reset "ans" in between.

I'll leave the solution of the problem to you, OP, as this smells a bit too much like homework for helping you up to that level.

---

