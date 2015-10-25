# 11-Clever-Methods-of-Overfitting-and-how-to-avoid-them

“Overfitting” is traditionally defined as training some flexible representation so that it memorizes the data but fails to predict well in the future
overfitting more generally as over-representing the performance of systems. There are two styles of general overfitting: over-representing performance on particular datasets and (implicitly) over-representing performance of a method on future datasets. 

We should all be aware of these methods, avoid them where possible, and take them into account otherwise. I have used “reproblem” and “old datasets”, and may have participated in “overfitting by review”—some of these are very difficult to avoid. 

# 1. Traditional overfitting:

 Train a complex predictor on too-few examples. 

Remedy:

1.Hold out pristine examples for testing.
2.Use a simpler predictor.
3.Get more training examples.
4.Integrate over many predictors.


# 2. Parameter tweak overfitting: 
Use a learning algorithm with many parameters. Choose the parameters based on the test set performance. 

For example, choosing the features so as to optimize test set performance can achieve this. 

Remedy: same as above 

# 3.Brittle measure

 Use a measure of performance which is especially brittle to overfitting. 

Examples: “entropy”, “mutual information”, and leave-one-out cross-validation are all surprisingly brittle. This is particularly severe when used in conjunction with another approach. 

Remedy: Prefer less brittle measures of performance. 

# 4. Bad statistics:
Misuse statistics to overstate confidences. 

One common example is pretending that cross validation performance is drawn from an i.i.d. gaussian, then using standard confidence intervals. Cross validation errors are not independent. Another standard method is to make known-false assumptions about some system and then derive excessive confidence. 

Remedy: Don’t do this.

# 5. Choice of measure:
Choose the best of Accuracy, error rate, (A)ROC, F1, percent improvement on the previous best, percent improvement of error rate, etc.. for your method. For bonus points, use ambiguous graphs. 

This is fairly common and tempting. 

Remedy: Use canonical performance measures. For example, the performance measure directly motivated by the problem. 

# 6.Incomplete Prediction
Instead of (say) making a multiclass prediction, make a set of binary predictions, then compute the optimal multiclass prediction. 

Sometimes it’s tempting to leave a gap filled in by a human when you don’t otherwise succeed. 

# 7.Human-loop overfitting:
 Use a human as part of a learning algorithm and don’t take into account overfitting by the entire human/computer interaction. 

This is subtle and comes in many forms. One example is a human using a clustering algorithm (on training and test examples) to guide learning algorithm choice. 

Remedy: Make sure test examples are not available to the human

# 8.Data set selection:

Chose to report results on some subset of datasets where your algorithm performs well. 

The reason why we test on natural datasets is because we believe there is some structure captured by the past problems that helps on future problems. Data set selection subverts this and is very difficult to detect. 

Remedy: Use comparisons on standard datasets. Select datasets without using the test set. Good Contest performance can’t be faked this way. 

# 9. Reprobleming: Alter the problem so that your performance improves.

Remedy: For example, take a time series dataset and use cross validation. Or, ignore asymmetric false positive/false negative costs. This can be completely unintentional, for example when someone uses an ill-specified UCI dataset. 

# 10.Old datasets:
Create an algorithm for the purpose of improving performance on old datasets. 

After a dataset has been released, algorithms can be made to perform well on the dataset using a process of feedback design, indicating better performance than we might expect in the future. Some conferences have canonical datasets that have been used for a decade… 

Remedy: Prefer simplicity in algorithm design. Weight newer datasets higher in consideration.

# 11.Overfitting by review

