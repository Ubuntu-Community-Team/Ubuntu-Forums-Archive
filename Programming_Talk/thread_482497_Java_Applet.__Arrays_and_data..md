---
title: "Java Applet.  Arrays and data."
date: 2007-06-23
forum: Programming Talk
---

### Post by huzzak on 2007-06-23
I'm trying to make a Java applet Tetris clone.  I've defined a TetrisPiece class that has arrays holding the various spawn positions and rotation changes for the individuals blocks of each Tetris piece.  They are defined by four (x,y) positions.

I had tried doing this with different classes all extending the TetrisPiece class, but since the only thing that differs in each is the data for where the blocks ought to be and consolidating this data makes my functions for checking rotation much simpler, I am trying to just have the one class with all the different data contained within.

My most recent attempt of getting this information consolidated into TetrisPiece was, I thought, pretty clever, and would have been perfect had it worked. I basically set it up so that the int arrays would be filled with the data needed for each tetris piece based on the code it was given by the calling function.  Apparently you can't define arrays in the way I tried to do so.

Any suggestions or ideas for different approaches?  Hopefully this is clear, but if it isn't, please ask me and I'll do my darndest to clarify.  Thanks.

```

public class TetrisPiece
{
	private TetrisBlock[] blocks;
	
	private int rotation_sequence;
	
	private int[] initial_position;
	
	// Changes in position for right rotations
	private int[] rot3to0;
	private int[] rot0to1;
	private int[] rot1to2;
	private int[] rot2to3;
	
	// Changes in position for left rotations
	private int[] rot0to3;
	private int[] rot1to0;
	private int[] rot2to1;
	private int[] rot3to2;
	
	public TetrisPiece (int tetroid_code)
	{
		switch (tetroid_code)
		{
			case 1: // I Tetroid
				initial_position = {3,0,4,0,5,0,6,0};
				rot3to0 = {-1,-2,0,-1,1,0,2,1};
				rot0to1 = {2,-1,1,0,0,1,-1,2};
				rot1to2 = {1,2,0,1,-1,0,-2,-1};
				rot2to3 = {-2,1,-1,0,0,-1,1,-2};
				rot0to3 = {1,2,0,1,-1,0,-2,-1};
				rot1to0 = {-2,1,-1,0,0,-1,1,-2};
				rot2to1 = {-1,-2,0,-1,1,0,2,1};
				rot3to2 = {2,-1,1,0,0,1,-1,2};
				break;
			case 2: // O Tetroid
				initial_position = {4,-1,5,-1,5,0,4,0};
				rot3to0 = {0,-1,1,0,0,1,-1,0};
				rot0to1 = {1,0,0,1,-1,0,0,-1};
				rot1to2 = {0,1,-1,0,0,-1,1,0};
				rot2to3 = {-1,0,0,-1,1,0,0,1};
				rot0to3 = {0,1,-1,0,0,-1,1,0};
				rot1to0 = {-1,0,0,-1,1,0,0,1};
				rot2to1 = {0,-1,1,0,0,1,-1,0};
				rot3to2 = {1,0,0,1,-1,0,0,-1};
				break;
			case 3: // T Tetroid
				initial_position = {3,0,4,0,5,0,4,-1};
				rot3to0 = {-1,-1,0,0,1,1,1,-1};
				rot0to1 = {1,-1,0,0,-1,1,1,1};
 
			...

```


Thanks for your help.

---

### Post by DougB1958 on 2007-06-23
I've done similar things before. I think part of the problem is that the "{...}" notation for an array can only be used to initialize the array in its declaration, you can't use it to assign a value to an array separately from the declaration, as you are doing. I have this dim memory that another part of the problem was that if you want to initialize an array that is a member of a class, then the array has to be static (but this was 5 years ago or so, so I may be remembering this part wrong, and/or newer versions of Java may have relaxed this). My basic trick to solving these problems was to put common array-manipulation code in a superclass (TetrisPiece, in your case), but then define subclasses to set up appropriate arrays, which can be passed to a constructor in the superclass.

Adapting these ideas to your situation, and just illustrating for one array, but hopefully you can extend the example to all, would look something like

```
public class TetrisPiece {
    ...
    private int[] rot3to0;
    ...
    public TetrisPiece( int[] valueForRot3To0, ... ) {
        rot3to0 = valueForRot3To0;
        ...
    }
    ...
}

public class ITetroid extends TetrisPiece {
    private static int[] iTetroidRot3To0 = {-1,-2,0,-1,1,0,2,1};
    public ITetroid() {
        super( ITetroidRot3To0, ... );
    }
}

```

You might, of course, want other features in the subclasses. And once you start thinking of each kind of tetris piece as a subclass of TetrisPiece, you might start to find that you don't need all the arrays in TetrisPiece -- perhaps methods in TetrisPiece can be written to get the information they now get from the arrays by calling small methods defined in the subclasses (I'm thinking of something called the "template method design pattern" here, if you want to look further into the idea).

---

### Post by huzzak on 2007-06-24
Thanks a ton DougB1958!  I modified my subclasses so that the array declarations were static and that made it so they could pass the information up to the superclass TetrisPiece.  Now I can work on clearing lines checking the rotation validity.

Thanks again.  I'll post a link to it here when I've got it all finished up.

---

