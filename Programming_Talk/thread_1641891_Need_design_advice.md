---
title: "Need design advice"
date: 2010-12-09
forum: Programming Talk
---

### Post by psld on 2010-12-09
Hi!
I am making a small stock trading game but I have come to a crossroad where I must choose a path (I am writing this in Java). This is my problem:

I have a **StockMarket**. It feels natural for the **StockMarket** to have a set of **Stocks**. There is also a couple of **StockTraders** in this. However, the **StockTraders** must know what **Stocks** there are. How do you suggest that I code this? Maybe my view of having the market consist of both stocks and traders are wrong?

Just to be clear, The market needs to access the stocks, and the market consists of both stocks and traders. The traders must also have access to the stocks but the very ugly solution I have to this is to let the traders be aware of the market that they lie in.

What do you think?

Thanks!

---

### Post by r-senior on 2010-12-09
With a brief look, it makes sense to me ... although I don't know all the rules you have in mind, so make allowances for that.

The market would have a collection of stocks available for trading on the market and a list of registered traders. Each trader would have a market (or markets) and a list of stocks they currently possess. A stock would have a market (or markets) and a list of traders who possess the stock.

```

public class Market {

    private Collection traders;
    private Collection availableStocks;

    ...
}

public class Stock {

    private Market market; // Collection if traded on multiple markets
    private Collection owningTraders;

    ...

}

public class Trader {

    private Market market; // Collection if more than one market
    private Collection ownedStocks;
    ...
    
}

```

You don't necessarily need all the relationships both ways. For example, you might not need a Stock to know which market it's in. Only the other way round.

If that was mapped to a database, you'd have a Market table, a Stock table, a Trader table and a StockTrader join table that holds the many-to-many relationship between Trader and Stock.

If you were to extend the complexity to allow multiple markets, you'd have corresponding join tables and need to thing about whether the a stock on one market is the same as the same stock on a different market.

I've suggested the generic Collection but you'd choose an appropriate List/Set implementation. Ordered and allows duplicates in a list. Unordered and no duplicates in a set.

When you come to implement the business logic, try to only have methods on an object that deal with that object, e.g. 

```


public class Trader {

    ...

    public BigDecimal getPortfolioValue() {
        for (Stock stock : ownedStocks) {
            // Sum the stock values
        }
    }  
 

```

For methods that make more complex use of multiple objects, make a "service" type object. 

For example:

```

public class TradingService {

    public void registerPurchase(Trader trader, Stock stock) {
        ...
        connection.startTransaction(); // e.g for database
        stock.addOwningTrader(trader);
        trader.addOwnedStock(stock);

        // Probably some calls to data access objects (DAOs) to save data ...

        connection.commit();
        ...
    }


``` 

The service then becomes the place to define database transactions if you are doing a database backend.

---

