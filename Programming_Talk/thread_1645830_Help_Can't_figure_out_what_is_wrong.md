---
title: "Help Can't figure out what is wrong"
date: 2010-12-15
forum: Programming Talk
---

### Post by Tomlana on 2010-12-15
I wrote a template class that is then inherited. I am reading in a file to create a table. The problem I am having is that when I try to print out the table out side of the constructor It prints out weired numbers

this is my code
```

template<class T>
class Prob3Table
{
	protected:
		int rows;                                 //Number of rows in the table
		int cols;                                 //Number of cols in the table
		T *rowSum;                                //RowSum array
		T *colSum;                                //ColSum array
		T *table;                                 //Table array
		T grandTotal;                             //Grand total
		void calcTable(void);                     //Calculate all the sums
	public:
		Prob3Table(char *,int,int);               //Constructor then Destructor
		~Prob3Table(){delete [] table;delete [] rowSum;delete [] colSum;};
		const T *getTable(void){return table;};
		const T *getRowSum(void){return rowSum;};
		const T *getColSum(void){return colSum;};
		T getGrandTotal(void){return grandTotal;};
};

template <class T>
Prob3Table<T>::Prob3Table(char *fle, int r, int c)
{
    T x;
    grandTotal=0;
    if (r>0){rows=r;}
    else{r=0;}
    if (c>0){cols=c;}
    else{cols=c;}
    ifstream infile(fle);
	T *table=new T[r*c];
    for(int i=0; i<r; i++)
    {
        for( int j=0; j<c; j++)
        {
                infile >> x;
                table[i*c+j]=x;
        }
    }
    cout<<"The origional Table after it is created:"<<endl;
    for(int i=0; i<r; i++)
    {
        for( int j=0; j<c; j++)
        {
                cout<<table[i*c+j]<<" ";
        }
        cout<<endl;
    }
    cout<<endl;
	infile.close();

}

template <class T>
void Prob3Table<T>::calcTable(void)
{
    T temp=0;
    rowSum=new T[rows];
    for(int i=0; i<cols; i++)
    {
        rowSum[i]=0;
    }
    colSum=new T[cols];
    for(int i=0; i<cols; i++)
    {
        colSum[i]=0;
    }

    for(int i=0; i<cols; i++)
    {
        for(int j=0; j<rows; j++ )
        {
            temp=temp+table[j*cols+i];
        }
        colSum[i]=temp;
        temp=0;
    }

    for(int i=0; i<rows; i++)
    {
        for(int j=0; j<cols; j++ )

        {
            temp=temp+table[i*cols+j];
        }
        rowSum[i]=temp;
        temp=0;
    }

    for(int i=0; i<cols; i++)
    {
        grandTotal=grandTotal+colSum[i];
    }
    cout<<grandTotal;
}




template<class T>
class Prob3TableInherited:public Prob3Table<T>
{
	protected:
		T *augTable;                                  //Augmented Table with sums
	public:
		Prob3TableInherited(char *,int,int);          //Constructor
		~Prob3TableInherited(){delete [] augTable;};  //Destructor
		const T *getAugTable(void){return augTable;};
};

template <class T>
Prob3TableInherited<T>::Prob3TableInherited(char *t,int ro,int co) : Prob3Table<T>(t,ro,co)
{
    this->calcTable();
    augTable= new T[(ro+1)*(co+1)];

    for(int i=0; i<ro; i++)
    {
        for( int j=0; j<co; j++)
        {
            augTable[i*co+j]= this->table[i*co+j];
        }
    }

    for(int i=0; i>ro; i++)
    {
        augTable[i*co+co]=this->rowSum[i];
    }

    for(int i=0; i>co; i++)
    {
        augTable[ro*co+i]=this->colSum[i];
    }

    augTable[ro*co]=this->grandTotal;

}


int main()
{
    cout<<"In problem # 3"<<endl<<endl;
    cout<<"Entering problem number 3"<<endl;
	int rows=5;
	int cols=6;
	char file[13]={"Problem3.txt"};
	Prob3TableInherited<int> tab(file,rows,cols);
	const int *naugT=tab.getTable();
	cout<<"The table:"<<endl;
	for(int i=0;i<rows;i++)
	{
		for(int j=0;j<cols;j++)
		{
			cout<<naugT[i*cols+j]<<" ";
		}
		cout<<endl;
	}
	cout<<endl<<"Augmented Table"<<endl;
	const int *augT=tab.getAugTable();
	for(int i=0;i<=rows;i++)
	{
		for(int j=0;j<=cols;j++)
		{
			cout<<augT[i*(cols+1)+j]<<" ";
		}
		cout<<endl;
	}
}

```

and this is the out put i get the first table is what i want and that is printed out from the constructor.

---

### Post by GeneralZod on 2010-12-15
```

	T *table=new T[r*c];

```

initialises a local variable, not the "table" member variable.

Edit:

Mistake here, too:

```

  rowSum=new T[rows];
  for(int i=0; i<cols; i++)
    {
        rowSum[i]=0;
    }

```

---

### Post by Tomlana on 2010-12-15
I don't see the error in the second one

---

### Post by Zugzwang on 2010-12-15
> **Tomlana said:**
> I don't see the error in the second one

"i<cols" should probably be "i<rows".

---

### Post by Tomlana on 2010-12-15
thanks i see it now

---

### Post by dwhitney67 on 2010-12-15
> **Tomlana said:**
> thanks i see it now

You could also have done:
```

#include <algorithm>

...

std::fill(rowSum, rowSum + rows, 0);

```
Also, learn to use the += operator; there's no need in your program for the use of a temp value when performing the summations.

---

