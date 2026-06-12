---
title: "Basic Java Program Help: Arrays"
date: 2013-10-29
forum: Programming Talk
---

### Post by WP6r8PA on 2013-10-29
So, just to put this out there, this was an assignment that was due last week I submitted incomplete. I'm just going back to try to figure out what I missed so I can catch up. I feel like there's something really obvious I'm missing and just needs more experienced eyes. So to clarify again, this is no longer homework, just for my own practice.

We were a[FONT=arial]sked to make an airline seating plan, no GUI just a text output. Normally I have no problem doing this stuff, but normally the professor gives more hints as to what we have to do. Here we were just given what the outcome should have, which is what threw me off I think. 
[/FONT]
The assignment:
[COLOR=#303030][FONT=arial]
[/FONT][/COLOR][I]Write a program that assigns seats on an airplane. Assume the airplane has 20 seats in first class (5 rows of 4 seats each, separated by an aisle) and 90 seats in economy class (15 rows of 6 seats each, separated by an aisle). Your program should take three commands: add passengers, show seating, and quit. When passengers are added, ask for the class (first or economy), the number of passengers traveling together (1 or 2 in first class; 1 to 3 in economy), and the seating preference (aisle or window in first class; aisle, center, or window in economy). Then try to find a match and assign the seats. If no match exists, print a message. Your solution should include a class Airplane that is not coupled with the Scanner or PrintStream classes. 

[/I]So, I got stuck pretty early, and I can tell my misunderstanding is with 2D arrays but I can't see how I should change it to fix the problem.
```
import java.lang.reflect.Array;



public class Airplane {
    [COLOR=#ff0000]private int rows = 0;[/COLOR]
[COLOR=#ff0000]    private int seats = 0;[/COLOR]
    int[][] Airplane = new int[rows][seats];
    
    public int getRows() {
        return rows;
    }
    
    public int getSeats() {
        return seats;
    }
    
    public void setRows(int rows) {
        this.rows = rows;
    }
    
    public void setSeats(int seats) {
        this.seats = seats;
    }
    
    [COLOR=#ff0000]public Airplane[][](int rows, int seats) {[/COLOR]
        this.rows = rows;
        this.seats = seats;
        return;
    }
    
}
```

Just to make it easier for anyone generous enough to attempt to lead me in the right direction I highlighted where the errors were. The reason I wanted to create Airplane.java the way I'm attempting to, is so I could then use (aggregate? is that the right use of the word?) it in the first class and econo class. We're practising inheritance v.s. aggregation and I'm assuming that was the intention of this assignment. Given an Airplane has a first class and an econo class, I thought aggregation would be the best way to go.

So, of course, because of the errors, this is what happened:
```
import java.lang.reflect.Array;import java.util.*;


public class AirplaneSeating {
    
    public AirplaneSeating() {
        [COLOR=#ff0000]Airplane FirstClassRight = new Array[2][2];
        Airplane EconoClassRight = new Airplane[7][3];[/COLOR]
``` 

I tried to do 2 things here:
1) Separate the rows by right and left, as there's an aisle in the middle, although maybe that wasn't the best strategy 
2) Create Airplane array objects. 

I'm totally lost. Any input is appreciated.

---

### Post by joe_7 on 2013-10-29
It's confusing to use a class name as a variable name. Also, you need to set the sizes before calling new. Start off with a null array and create it with new in the constructor. My version follows, as I probably would have written it:
 
```

[COLOR=#000000]import java.lang.reflect.Array;

public class Airplane
[/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#ff0000][COLOR=#000000]  private int rows = 0;[/COLOR][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#ff0000][COLOR=#000000]  private int seats = 0;[/COLOR][/COLOR][COLOR=#000000]
  private int data[][] = null;
    
  public int getRows()
  {
    return rows;
  }
    
  public int getSeats()
  {
    return seats;
  }
    
  public void setRows(int num)
  {
    rows = num;
  }
    
  public void setSeats(int num)
  {
    seats = num;
  }
    
  [/COLOR][COLOR=#ff0000][COLOR=#000000]public Airplane(int num_rows, int num_seats)
  {[/COLOR][/COLOR][COLOR=#000000]
    rows = num_rows;
    seats = num_seats;

    data = new int[rows][seats];
  } 
}
[/COLOR]
```

---

### Post by r-senior on 2013-10-29
I'm not sure what is going on here:

```
int[][] Airplane = new int[rows][seats];
```

You have declared a variable called Airplane that is a two-dimensional array. You seem to be confusing that with your class name. Also, the constructor you wrote is not a match for the Airplane class itself. It looks like it all fell apart when you tried to add the arrays.

Going back a step and taking the arrays out of the equation, your Airplane class has two properties: rows and seats. This might be a good starting point if each row had the same number of seats:

```
Airplane airplane = new Airplane(15, 6);
```

Unfortunately you have to deal with first class and economy, which have different numbers of seats in their respective rows. So maybe your Airplane class is actually a Section class?

```
Airplane airplane = new Airplane();
airplane.firstClass = new Section(5, 4);
airplane.economy = new Section(15, 6);

```

If you took this approach, you still need a method to work out whether seats are aisle, middle or window, based on the number of seats per row and the seat number. It doesn't feel like a good model to me, and that makes programming it too hard.

I see a SeatType enum and a Seat object:

```

public enum SeatType {
    WINDOW, MIDDLE, AISLE
}

public class Seat {
    private SeatType type;
    private boolean reserved;
    ...
}

```

Probably also a Row type and a Section enum, leading to your Airplane:

```

public enum Section {
    FIRST, ECONOMY
}

public class Row {
    private List<Seat> seats = new ArrayList<>();
    private Section section;
    ...
}

public class Airplane {
    private List<Row> rows = new ArrayList<>();
    ...
}

```

You'd construct rows for first class with 4 seats, rows for economy with 6 seats, then add them to the Airplane*. Then probably a SeatAllocationService** that you call from your main program. The main program deals with the input and output.

The seat allocation is then just a matter of iterating over the rows looking for matches and updating the reserved flag. You'd probably end up with a method on the row to test whether availability exists on that row for a given request and another to reserve seats in the row.

```

public class SeatAllocationService {

    /**
     * Allocate seats on an airplane in a preferred section, with a number of places and seating preference
     * @return true if seats could be allocated according to preference, otherwise false.
     */
    public boolean allocateSeats(Airplane airplane, Section section, int places, SeatType seatTypePreference) {
        for (Row row  : airplane.rowsMatchingSection(section) {
            if (row.hasAvailability(places, seatTypePreference) {
                ...
                return true;
            }
        }
        return false;
    }
}

```

I haven't thought it all the way through and there's probably a few twists and turns to negotiate before it would but that would be the approach I would take, i.e. model the problem more closely than just an Airplane class and a two-dimensional array. There's plenty of aggregation going on here: airplane has rows, rows have seats.

*Bonus points for using the builder design pattern to create the airplane instances and **programming to an interface on the service class.

---

