---
title: "Programming Assignment Help"
date: 2010-11-04
forum: Programming Talk
---

### Post by ProfessionalOPs on 2010-11-04
Hey Guys.. I am trying to do this program for my CS class and am having trouble with the logic. 

This is the assignment:

 A public method named intersection that takes a reference to a ClosedInterval object as a parame-
ter and returns a reference to a new ClosedInterval object. If the current ClosedInterval object and
the ClosedInterval object referenced by the parameter intersect, then that intersection forms a new
ClosedInterval. Create a new ClosedInterval object corresponding to that new ClosedInterval and re-
turn a reference to that new object. If the current ClosedInterval object and the ClosedInterval object
referenced by the parameter do not intersect, then return null.

The catch is that it must use if/else statements

any help appreciated.

---

### Post by Barrucadu on 2010-11-04
What progress have you made? What is the specific problem you are having?

---

### Post by ProfessionalOPs on 2010-11-04
Ok ill give you my code for the assignment so far

```
/**
 * Models a set of integers on a closed interval of a number line.
 * 
 * @author 
 * @author 
 * @version 10-26-10
 */
public class ClosedInterval
{
    /** Int field that is the leftEndpoint of the ClosedInterval */
    private int leftEndpoint;
    /** Int field that is the lenght if the ClosedInterval */
    private int closedIntervalLength;
    
    /**
     * Constructor that creates ClosedInterval with left end point and
     * closed interval length given.
     * 
     * @param leftEndpoint, the left end point.
     * @param closedIntervalLength, the lenght of the closed interval.
     */
    public ClosedInterval(int leftEndpoint, int closedIntervalLength)
    {
        this.leftEndpoint = leftEndpoint;
        this.closedIntervalLength = closedIntervalLength;
    }
    
    /**
     * Method that returns whether the given numPosition is in the 
     * closed interval.
     * 
     * @return boolean
     * @param numPosition, the point being tested.
     */
    public boolean contains(int numPosition)
    {
        int rightEndpoint = closedIntervalLength + leftEndpoint;
        boolean interval = false;
        if (numPosition <= rightEndpoint && numPosition >= leftEndpoint)
        {
            interval = true;
        }
        return interval;
    }
    
    /**
     * To string method that returns a string containing
     * the left and right end points in [0, 0] format
     * 
     * @return String
     */
    public String toString()
    {
        int rightEndpoint = closedIntervalLength + leftEndpoint;
        return "[" + leftEndpoint + ", " + rightEndpoint + "]";
    }
    
    /**
     * Method that returns a boolean of whether the given 
     * ClosedInterval object is the same as this ClosedInterval 
     * object.
     * 
     * @return boolean
     * @param other, a object of ClosedInterval typ that is tested.
     */
    public boolean isSame(ClosedInterval other)
    {
        boolean theSame = false;
        if (other.leftEndpoint == leftEndpoint &&
            other.closedIntervalLength == closedIntervalLength)
        {
            theSame = true;
        }
        return theSame;
    }
    
    /**
     * Mutator method that moves left and right endpoints by 
     * given amount.
     * 
     * @param amount, the amount to move the points by.
     */
    public void translate(int amount)
    {
         leftEndpoint = leftEndpoint + amount;
         
    }
    
    /**
     * Method that tests to see if to ClosedInterval objects 
     * intersect and then makes another ClosedInterval 
     * object containing the piece that was intersecting.
     * 
     * @return ClosedInterval
     * @param other, the other ClosedInterval object that is 
     *              supplied.
     */
    public ClosedInterval intersection(ClosedInterval other)
    {
        ClosedInterval interval = new ClosedInterval(0, 0);
       
        
        
        /*if (!this.contains(getOtherRightEndpoint(other)) && 
            !this.contains(other.leftEndpoint)){
                interval = null;
        } else if (this.contains(other.leftEndpoint)){
                interval = new ClosedInterval(other.leftEndpoint, 
                        getRightEndpoint());
        } else if (this.contains(getOtherRightEndpoint(other))){
                interval = new ClosedInterval(leftEndpoint, 
                        (getOtherRightEndpoint(other)));
        } else if (this.contains(other.leftEndpoint) && 
                this.contains(getOtherRightEndpoint(other))){
                interval = new ClosedInterval(other.leftEndpoint, 
                        getOtherRightEndpoint(other));
        } else if (other.contains(leftEndpoint) && 
                other.contains(getRightEndpoint())){
                interval = new ClosedInterval(leftEndpoint, 
                        getRightEndpoint());
        }
        */
        
       
       /*
       if (getRightEndpoint() < other.leftEndpoint || leftEndpoint > 
            other.getRightEndpoint()){
            interval = null;
        } else if (other.contains(leftEndpoint) && 
                other.contains(getRightEndpoint())){
            interval = new ClosedInterval(leftEndpoint, getRightEndpoint());
        } else if (contains(leftEndpoint)){
            interval = new ClosedInterval(leftEndpoint, other.closedIntervalLength);
        } else if (other.contains(leftEndpoint)){
            interval = new ClosedInterval(leftEndpoint, 
                other.closedIntervalLength);
        } else if (other.contains(getRightEndpoint())){
            interval = new ClosedInterval(other.leftEndpoint, 
                getOtherRightEndpoint(other));
        } else if (other.contains(leftEndpoint) && 
                other.contains(getRightEndpoint())){
            interval = new ClosedInterval(leftEndpoint, 
                getRightEndpoint());
        } else if (contains(other.leftEndpoint) && 
                contains(other.getRightEndpoint())){
            interval = new ClosedInterval(other.leftEndpoint, 
                other.closedIntervalLength);
        } else if (contains(other.getOtherRightEndpoint(other))){
            interval = new ClosedInterval(leftEndpoint, 
                getOtherRightEndpoint(other));
        } else if (other.contains(leftEndpoint) && 
                other.contains(getRightEndpoint())){
            interval = new ClosedInterval(leftEndpoint, getRightEndpoint());
       
        }
        
       return interval;
    }*/
    

        
      return interval;
    }
    
    /**
     * Acessor method that returns the left end point.
     * 
     * @return int
     */
    public int getLeftEndpoint()
    {
        return leftEndpoint;
    }
    
    /**
     * Accessor method that returns the right end point.
     * 
     * @return int
     */
    public int getRightEndpoint()
    {
       int rightEndpoint = closedIntervalLength + leftEndpoint;
       return rightEndpoint;
    }
    
    /**
     * Accessor method that returns and integer containing
     * others right end point
     * 
     * @return int
     * @param other the ClosedInterval object that is given
     * to get right end point of.
     */
    private int getOtherRightEndpoint(ClosedInterval other)
    {
        int otherRightEndpoint = other.closedIntervalLength + 
                other.leftEndpoint;
        return otherRightEndpoint;
    }
}

```

---

### Post by Barrucadu on 2010-11-04
Ok, well, the following Java-ish pseudocode should do it:

```
if (this.contains (other.left))
{
    if (this.contains (other.right))
    {
        return closedInterval (other.left to other.right);
    } else {
        return closedInterval (other.left to this.right);
    }
} else if (other.contains (this.left)) {
    if (other.contains (this.right))
    {
        return closedInterval (this.left to this.right);
    } else {
        return closedInterval (this.left to other.right);
    }
} else {
    return null
}
```

Unless I've misunderstood something. You could also get rid of the many return statements:

```
int left = -1;
int right = -1;

if (this.contains (other.left))
{
    left = other.left;
    if (this.contains (other.right))
    {
        right = other.right;
    } else {
        right = this.right;
    }
} else if (other.contains (this.left)) {
    left = this.left;
    if (other.contains (this.right))
    {
        right = this.right;
    } else {
        right = other.right;
    }
} else {
    return null
}

return closedInterval (left to right)
```

Though whether that's more readable is debatable. I prefer the former.

---

### Post by ProfessionalOPs on 2010-11-04
OK thanks I will try it out and get back to you.

---

### Post by ProfessionalOPs on 2010-11-04
Ok thankyou this worked great.

this is my code:
```
 public ClosedInterval intersection(ClosedInterval other)
    {
        if (this.contains (other.getLeftEndpoint()))
        {
            if (this.contains (other.getRightEndpoint()))
            {
                return new ClosedInterval(other.getLeftEndpoint(), other.closedIntervalLength);
            } else {
                return new ClosedInterval(other.getLeftEndpoint(), this.closedIntervalLength);
            }
        } else if (other.contains (this.getLeftEndpoint())){
            if (other.contains (this.getRightEndpoint()))
            {
                return new ClosedInterval (this.getLeftEndpoint(), this.closedIntervalLength);
            } else {
                return new ClosedInterval (this.getLeftEndpoint(), other.closedIntervalLength);
            }
        } else {
            return null;
        }
    }
```

Only one failed:...

 PASSED: Creating interval with left endpoint -5: [-5, -3]
PASSED: Creating interval with right endpoint -3: [-5, -3]
PASSED: toString() with interval [-5, -3]: [-5, -3]
PASSED: [-5, -3] is the same as [-5, -3]
PASSED: [-5, -3] is the same as [-5, -3]
PASSED: The interval [2, 4] includes 3
PASSED: The interval [2, 4] does not include 7
PASSED: The interval [2, 4] does not include -2
PASSED: The interval [2, 4] includes 2
PASSED: The interval [2, 4] includes 4
PASSED: The interval [-5, 5] includes 0
PASSED: The interval [-5, 5] includes -1
PASSED: The interval [-5, 5] includes 1
PASSED: The intersection of [2, 4] and [-1, 1] is empty (null): null
FAILED: The intersection of [2, 4] and [1, 3] is [2, 3]: [2, 4]
PASSED: The intersection of [2, 4] and [-1, 9] is [2, 4]
PASSED: The intersection of [2, 4] and [2, 3] is [2, 3]: [2, 3]
PASSED: The intersection of [2, 4] and [2, 12] is [2, 4]
PASSED: The intersection of [2, 4] and [5, 15] is empty (null): null
PASSED: [2, 4] translated by 5 results in [7, 9]
PASSED: [2, 4] translated by -5 results in [-3, -1]
-------------------------------------------------------------------------------
Tests executed:    21
     Successful:   20
     Unsuccessful: 1


any idea on what is causing this one to fail?

---

### Post by Barrucadu on 2010-11-05
Your test looks wrong.

**edit:** Oops, misread the output. Not sure why it's doing that.

---

### Post by s.fox on 2010-11-05
Hello,

From the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")

> Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

Sorry but thread closed.

---

