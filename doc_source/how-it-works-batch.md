# Get Inferences for an Entire Dataset with Batch Transform<a name="how-it-works-batch"></a>

To get inferences for an entire dataset, use batch transform\. With batch transform, you create a batch transform job using a trained model and the dataset, which must be stored in Amazon S3\. Amazon SageMaker saves the inferences in an S3 bucket that you specify when you create the batch transform job\. Batch transform manages all of the compute resources required to get inferences\. This includes launching instances and deleting them after the batch transform job has completed\. Batch transform manages interactions between the data and the model with an object within the instance node called an agent\.

Use batch transform when you:
+ Want to get inferences for an entire dataset and index them to serve inferences in real time
+ Don't need a persistent endpoint that applications \(for example, web or mobile apps\) can call to get inferences
+ Don't need the subsecond latency that Amazon SageMaker hosted endpoints provide

You can also use batch transform to preprocess your data before using it to train a new model or generate inferences\.

The following diagram shows the workflow of a batch transform job:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/sagemaker/latest/dg/images/batch-transform-v2.png)

To perform a batch transform, create a batch transform job using either the Amazon SageMaker console or the API\. Provide the following:
+ The path to the S3 bucket where you've stored the data that you want to transform\.
+ The compute resources that you want Amazon SageMaker to use for the transform job\. *Compute resources* are machine learning \(ML\) compute instances that are managed by Amazon SageMaker\.
+ The path to the S3 bucket where you want to store the output of the job\.
+ The name of the Amazon SageMaker model that you want to use to create inferences\. You must use a model that you have already created either with the [CreateModel](API_CreateModel.md) operation or the console\.

The following is an example of what a dataset file might look like\. 

```
An example of input file content:
                Record1-Attribute1, Record1-Attribute2, Record1-Attribute3, ..., Record1-AttributeM
                Record2-Attribute1, Record2-Attribute2, Record2-Attribute3, ..., Record2-AttributeM
                Record3-Attribute1, Record3-Attribute2, Record3-Attribute3, ..., Record3-AttributeM
                ...
                RecordN-Attribute1, RecordN-Attribute2, RecordN-Attribute3, ..., RecordN-AttributeM
```

A record is a single input data unit, for information on how to delimit records for batch transform jobs, see `SplitType` in [TransformInput](API_TransformInput.md)\.

For an example of how to use batch transform, see [Step 6\.2: Deploy the Model with Batch Transform](ex1-batch-transform.md)\.

## How It Works: Next Topic<a name="how-it-works-batch-next-topic"></a>

[Validate a Machine Learning Model](how-it-works-model-validation.md)