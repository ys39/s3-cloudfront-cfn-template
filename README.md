# S3-Cloudfront CloudFormation Template
* Diagram

  ![Diagram](s3-cloudfront.jpg)

* This is a CloudFormation template to create a S3 bucket and CloudFront distribution.
* Access files stored in S3 via CloudFront.

## Resources
* S3Bucket
  - This resource creates a private S3 bucket. The bucket name is based on the values specified for the Prefix and BucketName parameters. This bucket has public access blocked and server-side encryption enabled by default.

* S3BucketPolicy
  - This policy allows GetObject requests from a specific CloudFront distribution to the S3 bucket.

* S3IAMPolicy
  - This IAM policy allows specific access to the S3 bucket (ListAllMyBuckets for all buckets, ListBucket for a specific bucket, and GetObject/PutObject/DeleteObject for a specific bucket). This policy is associated with the S3IAMGroup.

* S3IAMGroup
  - This IAM group is named based on the Prefix parameter.

* S3IAMUser
  - This IAM user belongs to the S3IAMGroup. The username is based on the Prefix parameter.

* CloudFront
  - This resource creates a CloudFront distribution. This distribution uses the S3 bucket as its origin.

* OAC
  - Origin Access Control (OAC) manages traffic between CloudFront and S3.

## S3 Bucket delete
* For Amazon S3 buckets, all objects in the bucket must be deleted for the deletion to succeed.

## S3 Access Keys
* S3 access keys are created from the AWS console. However, if you use the Secret Manager, you can create them in cloudformation.