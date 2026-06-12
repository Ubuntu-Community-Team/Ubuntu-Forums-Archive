---
title: "Creating Simple Maps using R"
date: 2014-01-30
forum: Programming Talk
---

### Post by RichardET on 2014-01-30
I can already create simple state level maps using R - here is an example:
richard <- function()
{
  data <- read.csv( "/home/rthornto/R/NST_EST2012_ALLDATA.csv")
  print(dim(data))
  data$popnames <- as.character(data$Name)
  data$pop2000 <- data$CENSUS2010POP
  x <- data$pop2000
  x[x < 1000000] <- "red"
  x[x >= 1000000 & x < 2000000] <- "yellow"
  x[x >= 2000000 & x < 3000000] <- "blue"
  x[x >= 3000000 & x < 4000000] <- "green"
  x[x >= 4000000 & x < 5000000] <- "purple"
  x[x >= 5000000 & x < 8000000] <- "brown"
  x[!(x %in% c("red", "yellow", "blue", "green", "purple","brown"))] <- "cyan"
  data$popdich <- x
  library(maps)
  library(mapproj)
  mapnames <- map("state", plot=FALSE)$names
  mapnames.state <- ifelse(regexpr(":",mapnames) < 0, mapnames,
                           substr(mapnames, 1, regexpr(":",mapnames)-1))
  popnames.lower <- tolower(data$popnames)
  cols <- data$popdich[match(mapnames.state, popnames.lower)]
  map("state", fill = TRUE, col = cols, proj="albers", param = c(35,50))
  #title("48 States by Population using 2010 Estimates")
 # title(main = list("48 States by Population using 2010 Estimates", cex = 1.5,
               #     col = "red", font = 3))
  title("Lower 48 States by Population using 2010 Estimates", sub = "by Richard Thornton",
       cex.main = 1,   font.main= 4, col.main= "blue",
        cex.sub = 0.75, font.sub = 3, col.sub = "red")

}
data <- richard()

[ATTACH]249929[/ATTACH]

But how would one do something similar with county, state?  I used data afrom census.gov, very easy to download.

Are there any published books on map building in R?

---

### Post by philinux on 2014-01-30
Moved to Programming Talk.

Not a Cafe type thread.

---

