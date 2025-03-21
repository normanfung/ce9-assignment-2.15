# ce9-assignment-2.15

## What is needed to authorize your EC2 to retrieve secrets from the AWS Secret Manager?

To allow an EC2 instance to retrieve secrets from AWS Secrets Manager, you need to perform the following steps:

1. Attach an IAM Role to Your EC2 Instance:
Create an IAM role that grants permission to access AWS Secrets Manager and attach it to the EC2 instance.
The IAM role will be used by the EC2 instance to assume permissions to retrieve secrets.
2. Create an IAM Policy for Secrets Manager Access:
This policy defines the permissions that your EC2 instance has for interacting with Secrets Manager.
The permissions needed are typically secretsmanager:GetSecretValue to retrieve the secret value and possibly secretsmanager:DescribeSecret to view metadata about the secret.
3. Attach the IAM Policy to the IAM Role:
The IAM role attached to the EC2 instance must have the policy granting access to Secrets Manager.


## Derive the IAM policy (i.e. JSON)?
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "secretsmanager:GetSecretValue",
        "secretsmanager:DescribeSecret"
      ],
      "Resource": "arn:aws:secretsmanager:us-west-2:<AWS-ACCOUNT>:secret:prod/cart-service/credentials"
    }
  ]
}
```
