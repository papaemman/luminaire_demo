# luminaire_demo

There is a bug 🐛 in the [zillow/luminaire](https://github.com/zillow/luminaire).

## Description

Data Exploration module doesn't work for time series with frequency 'W' because of a missing variable (tc_window_length).


## Solution 

**Initial code**

```{python}
tc_window_len_dict = {
      'H': 24,
      'D': 7,
  }

if freq in ['H', 'D']:
    self.tc_window_length = tc_window_len_dict.get(freq)
```


**v1**

```{python}
tc_window_len_dict = {
      'H': 24,
      'D': 7
     }
self.tc_window_length = tc_window_len_dict.get(freq) if freq in ['H', 'D'] else None
```

**v1**

```{python}
tc_window_len_dict = {
    'H': 24,
    'D': 7,
    'W':4
}
self.tc_window_length = tc_window_len_dict.get(freq) if freq in ['H', 'D', 'W'] else None
```