# Hosting a Static Website with a Custom Domain Name using Amazon S3, Route 53, and CloudFront

This project demonstrates how to host a static website using Amazon Web Services (AWS) services like Amazon S3, Route 53, and CloudFront. It covers setting up a custom domain name, enabling HTTPS using CloudFront, and ensuring optimal performance and security for your static website.

## Prerequisites

Before you begin, ensure you have the following:

- An AWS account with appropriate permissions to create S3 buckets, CloudFront distributions, and manage Route 53.
- Your static website files ready to be uploaded to an S3 bucket.

## Steps to Host a Static Website

### 1. Upload Website Files to S3

1. **Create an S3 Bucket**:
   - Log in to AWS Management Console.
   - Go to Amazon S3 and create a new bucket with a globally unique name (e.g., `example.com`).
  
![Screenshot 2024-06-17 040945](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/6c183ca6-0ab9-4ac8-83cd-631c6f5d679e)


2. **Upload Website Files**:
   - Upload your static website files (HTML, CSS, JS, images, etc.) to the S3 bucket.
   - Ensure the files are publicly accessible by setting appropriate permissions.
  
![Screenshot 2024-06-17 041215](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/c49844a3-14e7-4a8b-8d93-a786e6cd87e6)

![Screenshot 2024-06-17 041031](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/729ecd59-0e72-4e84-a3e0-3d92121f7d68)

3. **Enable Static Website Hosting**:
   - In the S3 bucket properties, enable static website hosting.
   - Set the index document (e.g., `index.html`) and error document if needed.
  
![Screenshot 2024-06-17 152018](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/46d972a7-1c8a-45c7-b743-c660df39cc4c)

### 2. Configure Route 53 for the Custom Domain

1. **Register Domain Name (if not already)**:
   - Go to AWS Route 53 or any domain registrar of your choice (in my case: GoDaddy) and register your domain name (e.g., `example.com`).

2. **Create Hosted Zone in Route 53**:
   - Go to Route 53 in the AWS Management Console.
   - Create a new hosted zone for your domain name (`example.com`).

3. **Create Record Sets**:
   - Create a record set for your domain and subdomains (e.g., `www.example.com`).
   - For each record set, choose type `A - IPv4 address` and alias to your S3 static website endpoint.
  
![Screenshot 2024-06-17 152712](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/3586d148-fc36-4b3c-8a59-09ccdfbd2277)

### 3. Set Up CloudFront Distribution for HTTPS

1. **Create CloudFront Distribution**:
   - Go to AWS CloudFront in the AWS Management Console.
   - Create a new web distribution.
   - Set the origin domain name to your S3 bucket endpoint (e.g., `example.com.s3.amazonaws.com`).

2. **Configure Distribution Settings**:
   - Set the default root object (e.g., `index.html`).
   - Specify alternate domain names (e.g., `example.com`, `www.example.com`).
   - Enable HTTPS by choosing a custom SSL certificate (you can use AWS Certificate Manager to request or import a certificate).

3. **Deploy Your CloudFront Distribution**:
   - Wait for the distribution to deploy (this may take some time).
   - Once deployed, CloudFront will provide you with a domain name (e.g., `dxxxxxxxxxxxx.cloudfront.net`).
  
![Screenshot 2024-06-17 161840](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/fd7c6c20-73cb-452a-b5d7-b1cc566029fe)

![Screenshot 2024-06-17 042030](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/9165e0e7-0a00-4b6c-b151-b93cbdaf7456)

![Screenshot 2024-06-17 042212](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/b6967a4a-2f5d-4a52-863c-1a8f5c82a78b)

### 4. Test and Verify

1. **Test Your Website**:
   - Access your website using both HTTP and HTTPS protocols.
   - Ensure all content loads correctly and there are no mixed content warnings (if using HTTPS).

2. **DNS Propagation**:
   - DNS changes may take some time to propagate. Use tools like `dig` or online DNS checkers to verify DNS records.
  
### Website is up and running.

![Screenshot 2024-06-17 035504](https://github.com/shivxm03/AWS-StaticWebsite-Hosting/assets/157244434/76229b0d-26cd-4965-a1e4-f8984413b45a)

### 5. Additional Considerations

- **Security Headers**: Consider adding security headers like Content Security Policy (CSP) and HTTP Strict Transport Security (HSTS) to enhance security.
- **Performance Optimization**: Use CloudFront caching options and compression settings to improve website performance.

## Resources

- [Amazon S3 Documentation](https://docs.aws.amazon.com/s3/)
- [Amazon Route 53 Documentation](https://docs.aws.amazon.com/Route53/)
- [Amazon CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)
- [AWS Certificate Manager Documentation](https://docs.aws.amazon.com/acm/)

## Contributing

Contributions are welcome! If you find any issues or have improvements, please open an issue or submit a pull request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
