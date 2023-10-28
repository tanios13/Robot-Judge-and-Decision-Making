# Essentials takeaways

1. **03**: Using two highly correlated features in **linear regression** doesn't prevent you from building a model, it can lead to issues related to interpretation, stability, and generalization. It's always a good idea to check for multicollinearity when building linear regression models and address it appropriately:

    Intuition:
    
    Imagine you're trying to understand the impact of study hours and tutoring hours on exam scores. Let's assume for this example that whenever a student studies for an hour, they also receive an hour of tutoring. This means the number of study hours and tutoring hours are essentially the same (highly correlated).
    Now, you want to know the separate effects of each - studying and tutoring - on the exam score. However, since they always occur together, it's hard to tell which one is really having the effect on the score. If we collect new data where the correlation between study hours and tutoring hours changes slightly, our model's predictions could change dramatically. This is because the model is uncertain about the real impact of each individual feature.

    Mathematical Proof: 

    Consider the simple linear regression equation:
    $$ y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \epsilon $$

    Where:
    - \( y \) is the dependent variable.
    - \( x_1 \) and \( x_2 \) are the independent variables.
    - \( \beta_0, \beta_1, \beta_2 \) are the coefficients.
    - \( \epsilon \) is the error term.

    If \( x_1 \) and \( x_2 \) are highly correlated, i.e., \( x_2 \) can be expressed as:
    $$ x_2 = x_1 + \delta $$

    Then our linear regression equation transforms to:
    $$ y = \beta_0 + \beta_1x_1 + \beta_2(x_1 + \delta) + \epsilon $$
    $$ \implies y = \beta_0 + (\beta_1 + \beta_2)x_1 + \beta_2\delta + \epsilon $$

    From this equation, we can infer:
    1. The combined effect of the independent variable \( x_1 \) is now \( \beta_1 + \beta_2 \) due to the correlation between \( x_1 \) and \( x_2 \).
    2. The model struggles to differentiate between the impacts of \( x_1 \) and \( x_2 \).

    The ordinary least squares (OLS) method used to estimate the coefficients is defined as:
    $$ \beta = (X^TX)^{-1}X^Ty $$

    Where:
    - \( X \) is the matrix of independent variables.
    - \( y \) is the vector of the dependent variable.

    For highly correlated \( x_1 \) and \( x_2 \), the matrix \( X^TX \) approaches singularity, leading its determinant to near zero. In such scenarios, the inverse \( (X^TX)^{-1} \) is either non-existent or exhibits high values, resulting in inflated variances for the estimates of \( \beta_1 \) and \( \beta_2 \), making them unstable.

    In conclusion, multicollinearity, from a mathematical standpoint, affects the estimation of coefficients by impacting the stability of the inverse of \( X^TX \) in OLS estimation, leading to unstable and often inflated coefficient estimates.

2. **03**: How to make a linear regression:
    1. Which metrics for measuring regression quality.
    2. Which models to use.
    3. How fine tune the model.

3. **05** : In the context of a classification problem, a threshold is a value which determines whether a given instance prediction is positive or negative based on the predicted probability or score.
By varying the threshold, you can control the trade-off between precision and recall. A lower threshold will classify more instances as positive, increasing recall but possibly decreasing precision. Conversely, a higher threshold will classify fewer instances as positive, possibly increasing precision but decreasing recall.