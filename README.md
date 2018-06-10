# parallel-statistics
Single-pass, parallel statistics algorithms for mean, variance, and standard deviation. See the rs.py file for example usage. 

This code enables the ability to split up datasets and in parallel compute some descriptive statistics. Here is an example from the test_suit fuction in rs.py. 

```python
    # Setup test data
    
    t1 = np.random.randint(9, size=(1,2000)) * 8.9
    t1 = list(t1[0])


    t2 = np.random.randint(20, size=(1,200)) * 8.9
    t2 = list(t2[0])


    t3 = np.random.randint(100, size=(1,500)) * 8.9
    t3 = list(t3[0])

    t4 = t1 + t2 + t3 



    # crate instances of data structure 
    h1 = get_rolling_stats(t1)
    h2 = get_rolling_stats(t2)
    h3 = get_rolling_stats(t3)

    h_1_2 = get_rolling_stats(t1 + t2)
    h4 = get_rolling_stats(t4)

    # Test map opperation and addition
    l_rs = [h1,h2,h3]
    h5 = aggrate_rolling_values(l_rs)

    # Test addition 
    h6 = (h1 + h2) + h3
