## FIGURE 4

<img src="/Graphics/Figure_4.jpg" alt="Figure 2" width="400"/>

### Scatterplot with linear regression line and 95% confidence interval

Activate packages:
```
library(ggplot2)
```
Import data (see example data [here](https://github.com/tylerdevos/terrapin_nest_predation/blob/main/Data/count_data_2020.csv)):
```
counts_2020 <- read.csv("~/Desktop/Spring 2022/Nest predation project/Clean Data/count_data_2020.csv")
```
Remove rows with missing values for either variable of interest:
```
counts_2020.1 <- subset(counts_2020, counts_2020$predated_total!='NA')
counts_2020.2 <- subset(counts_2020, counts_2020$predators_total!='NA')
```
Generate graph and export to working directory as a PDF:
```
p4 <- ggplot(counts_2020.2, aes(x=predators_total, y=predated_total)) +
  geom_point(pch=20, cex=2) +
  geom_smooth(method="lm", color="red4", lwd=0.5, linetype="solid") +
  scale_x_continuous(limits=c(0,9), breaks=seq(0,9,1)) +
  scale_y_continuous(limits=c(0,32), breaks=seq(0,30, 5)) +
  labs(x="Predator sightings on camera", y="Predated nests") +
  ggtitle("2020") +
  theme_minimal() +
  theme(plot.title=element_text(hjust=0.5), axis.line=element_line(), legend.position='none', panel.grid.major=element_blank(), panel.grid.minor=element_blank(), text=element_text(family="Times New Roman"))
ggsave(p4, filename="predation_regression_2020.pdf", device=cairo_pdf, width=3.15, height=2.1, units="in")
```
### [<<< Back to Figure 3](https://github.com/tylerdevos/terrapin_nest_predation/blob/main/Figure_3.md) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; [To Figure 5 >>>](https://github.com/tylerdevos/terrapin_nest_predation/blob/main/Figure_5.md)
