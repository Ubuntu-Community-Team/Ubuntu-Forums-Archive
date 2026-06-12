---
title: "[SOLVED] Qt: Signal and slot with different parameters"
date: 2007-09-26
forum: Programming Talk
---

### Post by akudewan on 2007-09-26
Hello,

I'm making a Sudoku (solving/generating) program in Qt. Now, I'm just a beginner as a programmer, and I have no experience with Qt. I'm stuck in a strange situation. I want to connect a signal and slot with different parameters.

My grid is made up of an array of QLineEdits, and here's how I'm making the connections:
```

/* Making connections */
	for(minigrid=0;minigrid<9;minigrid++)
	{
		for(row=0;row<3;row++)
		{
			for(column=0;column<3;column++)
			{
				connect(box[minigrid][row][column], SIGNAL(returnPressed()), this, SLOT(checkInput(int, int int)));
			}
		}
	}

```

The 3 parameters of checkInput() are the minigrid, row and column numbers of the respective box in the grid. Qt doesn't accept Signals and Slots with different parameters, so how do I go about doing this?
Do I:
1) Overload returnPressed() of QLineEdit ? Is this even possible?
2) Create my own Signal in the Grid class? If so, how do I connect this signal to returnPressed() ? (if I do, then both will need to have void parameters. What how do I get the values of minigrid, row and column then?)
3) Change the structure of my grid? Use 81 connect statements ?
4) Can I subclass QLineEdit, and make my own signal in it?

Any help with this will be greatly appreciated...

---

### Post by the_unforgiven on 2007-09-27
The easiest way is to subclass QLineEdit and write a custom signal in it.
Other way would be to find a better alternative to QLineEdit. I don't know anything about your code, so I cannot comment on what would be an alternative.

HTH ;)

---

### Post by akudewan on 2007-09-28
> **the_unforgiven said:**
> The easiest way is to subclass QLineEdit and write a custom signal in it.
Other way would be to find a better alternative to QLineEdit. I don't know anything about your code, so I cannot comment on what would be an alternative.

HTH ;)

Thanks mate!

I made a subclass of QLineEdit, and included the data members minigrid, row & column that tell the position of the box. Then I used a Slot that simply emits the signal with the parameters I need.

```

/* the subclass */
class SLineEdit: public QLineEdit
{
	Q_OBJECT
	public:
		int minigrid, row, column;
		void setPosition(int, int, int);
		SLineEdit(QWidget *parent = 0);
	private slots:
		void dataEntered();
	signals:
		void sendForCheck(int, int, int);
};

```

```

/* its implementation */
SLineEdit::SLineEdit(QWidget *parent) : QLineEdit(parent)
{
}

void SLineEdit::setPosition(int mg, int r, int c)
{
	this->minigrid = mg;
	this->row = r;
	this->column = c;
}

void SLineEdit::dataEntered()
{
	emit sendForCheck(this->minigrid, this->row, this->column);
}

```

```

/*and the connections */
for(int minigrid=0;minigrid<9;minigrid++)
	{
		for(int row=0;row<3;row++)
		{
			for(int column=0;column<3;column++)
			{
				connect(box[minigrid][row][column], SIGNAL(returnPressed()), box[minigrid][row][column], SLOT(dataEntered()));
				
				connect(box[minigrid][row][column], SIGNAL(sendForCheck(int, int, int)), this, SLOT(checkInput(int, int, int)));
				
			}
		}
	}

```

It feels so good to finally get this working after breaking my head over it for 2 days...
:)

---

### Post by the_unforgiven on 2007-09-30
Sounds good. Congrats ;)

---

### Post by ihavenoname on 2008-06-03
thanks for posting your solution this has helped me out.

---

