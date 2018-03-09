## Welcome to GitHub Pages
---
title: "My R Programming Blog - The Dplyr Library & Piping"
author: "Sai Ranganathan"
date: "3/8/2018"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

Today, I would like to talk about an R programming principle which I found to be the most useful when taking INFO 201. 

One method that I found to be very helpful that had helped me work with the manipulation of data, especially within the form of data frames was the "dplyr" library. The dplyr method is a grammar of data manipulation, providing a consistent set of verbs that help you solve the most common data maniputation challenges. The bottom methods help you show you what you can do to manipulate data within a given data frame. 

  - mutate() adds new variables that are functions of existing            variables
  - select() picks variables based on their names.
  - filter() picks cases based on their values.
  - summarise() reduces multiple values down to a single summary.
  - arrange() changes the ordering of the rows.
  
One example of the dplyr method in use is shown in the code below. 

```{r binge_data}
library("dplyr")
name <- c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune")
type <- c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
          "Terrestrial planet", "Gas giant", "Gas giant", "Gas giant", "Gas giant")
diameter <- c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation <- c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings <- c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

# Create a data frame from the vectors
planets_df <- data.frame(name, type, diameter, rotation, rings)

planets_df <- select(planets_df, name, type, diameter)
planets_df <- filter(planets_df, diameter > 4)

```

The above data manipulation can also be done using piping, which is where you use the keyphrase "%>%" in order to make the process more efficient and without repeating certain terminology. A similar code to the one above is done with piping. Note how much cleaner the code looks, and how much faster it would be to process the data. 

```{r, data_with_piping}
planets_df %>% select(name,type,diameter) %>% filter(diameter > 4)
```

Overall, the dplyr method and piping are well known and commonly used methods within the R programming world, and was one of the most useful concepts that I learend in terms of data analysis and manipulation. 


