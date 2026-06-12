---
title: "Segmentation fault (core dumped) code::blocks"
date: 2015-04-29
forum: Programming Talk
---

### Post by martin156 on 2015-04-29
Hi all, I'm having issues with my code below when I try to cout yearly_avg under the function DisplayFiveStar function. When calling the function in main and running the  program i get the "Segmentation fault (core dumped) message. I believe it has to do with the program trying to access memory that it shouldn't? Either way I'm having some difficulty locating the main issue with this. Thanks for any help!

```

using namespace std;

const int MONTHS = 12;
const int NUM_STORES = 25;

bool GetStoreData(string[], double[][MONTHS]);
//bool DisplayReport(const string[], const double [][MONTHS]);
double YearlyTotal(double[][MONTHS], double[]);
double MonthlyAverage(double[][MONTHS], double[]);
double DisplayFiveStar(string[], double[]);

int main()
{
    bool success;
    string store_ids[NUM_STORES];
    double sales_data[NUM_STORES][MONTHS];
    double yearly[NUM_STORES];
    double monthly[NUM_STORES];

    success = GetStoreData(store_ids, sales_data);
    if(!success)
    {
        cout << "Input file open error." << endl;
        return 1;
    }

    //success = DisplayReport(store_ids, sales_data);
    //if(!success)
    //{
        //cout << "Output file open error." << endl;
      //  return 2;
    //}

    double month = MonthlyAverage(sales_data, monthly);
    double year = YearlyTotal(sales_data, yearly);
    double year_avg = DisplayFiveStar(store_ids, yearly);

    return 0;
}

bool GetStoreData(string ids[], double sales[][MONTHS])
{
    ifstream fin;

    bool success;

    fin.open("store_data.txt");

    if(!fin)
        success = false;
    else
    {
        success = true;
    }

    for(int row = 0; row < NUM_STORES; row++)
    {
        fin >> ids[row];
        //cout<< ids[row]<< " ";

        for(int column = 0; column < MONTHS; column++)
        {
            fin >> sales[row][column];
            //cout << sales[row][column]<<" ";
        }
        //cout<<endl;

    }

    fin.close();
    return success;
}

double MonthlyAverage(double sales[][MONTHS], double monthly[])
{
    double tally;
    double tally_avg;

    tally = 0;
    for(int row = 0; row < MONTHS; row++)
    {
        for(int column = 0; column < NUM_STORES; column++)
        {
            tally = tally + sales[column][row];
        }
        tally_avg = (tally / NUM_STORES);
        //cout << tally_avg << endl;
        tally = 0;
    }
    return tally_avg;
}

double YearlyTotal(double sales[][MONTHS], double yearly[])
{
    double tally;
    int yearly_location;

    tally = 0;
    for(int column = 0; column < NUM_STORES; column++)
    {
        for(int row = 0; row < MONTHS; row++)
        {
            tally = tally + sales[column][row];
        }
        //cout << tally << endl;
        yearly[yearly_location] = tally;
        tally = 0;
    }
    return tally;
}

double DisplayFiveStar(string ids[], double yearly[])
{
    double tally,
           yearly_avg;

    yearly = 0;
    for(int i = 0; i < NUM_STORES; i++)

        tally = tally + yearly[i];

        yearly_avg = (tally / NUM_STORES);
        cout << yearly_avg << endl;

    return yearly_avg;
}
```

---

### Post by Rocket2DMn on 2015-04-30
You should learn how to use gdb for debugging.

Are you sure that's where you're getting the segfault?  I see at least one place that could be causing it:
```
yearly[yearly_location] = tally;
```
yearly_location is never assigned a value (or incremented as expected) so could be anything.

---

