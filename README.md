# Assignment3 
## Sriya Reddy

In this assignment, I followed the following steps and obtained the results as shown. 
I first created three matrices to contain the names of the candidates, the ABC poll results and the NCB poll results as shown below. 

`name<-c("Jeb","Donald","Ted","Marco","Carly","Hillary","Berine")`

`ABC_political_poll_results<-c(4,62,51,21,2,14,15)`

`NCB_political_poll_results<-c(12,75,43,19,1,21,19)`

I then combined the three matrices using the `cbind` function in R and saved the result in a new matrix called `poll_results` as shown below. 

`poll_results <- cbind(name, ABC_political_poll_results, NCB_political_poll_results)`

`poll_results` contains:
```
name      ABC_political_poll_results NCB_political_poll_results
[1,] "Jeb"     "4"                        "12"                      
[2,] "Donald"  "62"                       "75"                      
[3,] "Ted"     "51"                       "43"                      
[4,] "Marco"   "21"                       "19"                      
[5,] "Carly"   "2"                        "1"                       
[6,] "Hillary" "14"                       "21"                      
[7,] "Berine"  "15"                       "19" 
```

Now, directly using `mean(poll_results)` does not work and I get 

```[1] NA
Warning message:
In mean.default(poll_results) :
  argument is not numeric or logical: returning NA
```

For this reason, i converted the matrix to a data frame using:

`poll_results.df <- data.frame(name, ABC_political_poll_results, NCB_political_poll_results)`

`poll_results.df` contains
```
name ABC_political_poll_results NCB_political_poll_results
1     Jeb                          4                         12
2  Donald                         62                         75
3     Ted                         51                         43
4   Marco                         21                         19
5   Carly                          2                          1
6 Hillary                         14                         21
7  Berine                         15                         19
```

Now, using `mean(poll_results.df)` also gives me a warning:

```
[1] NA
Warning message:
In mean.default(poll_results.df) :
  argument is not numeric or logical: returning NA
```

Trying to find the mean of numeric columns only, I used `mean(poll_results.df[,2:3])`. However, this also produced:

```
[1] NA
Warning message:
In mean.default(poll_results.df[, 2:3]) :
  argument is not numeric or logical: returning NA
```
However, I was able to use `mean(poll_results.df[, 2])` and `mean(poll_results.df[, 3])` to obtain the mean of individual columns.

```
> mean(poll_results.df[, 2])
[1] 24.14286
> mean(poll_results.df[, 3])
[1] 27.14286
```

To obtain the means of both the columns together, I used `colMeans(poll_results.df[, 2:3])` which gave me:

```
> colMeans(poll_results.df[, 2:3])
ABC_political_poll_results NCB_political_poll_results 
                  24.14286                   27.14286
```

Hence, the final mean is: **24.14286** for ABC poll results and **27.14286** for NCB poll results. 











