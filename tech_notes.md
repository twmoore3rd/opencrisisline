#AWS EC2 t2.micro instance
1.  Ran on two servers using two EC2 micro instances
1.  Web Server
    1.  Setup from following https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-lamp-amazon-linux-2.html
        1. **NOTE:** Linux 2 AMI not Linux AMI
        1.  Centos/Red Hat based (`cat /etc/os-release`)
        1.  Probably want to open ssh port (22)
# Mint 19(.1?)
1.  For local development purposes only so PhpStorm could be used
1.  PHP install: `sudo apt-get install php libapache2-mod-php php-mysql`
1.  `sudo apt-get install build-essential`
        1.  Addresses `configure: error: C compiler cannot create executables` issue in the  `./configure --prefix=$HOME/curl` step
1.  Believe Apache install was done: `sudo apt-get install apache2`
    1.  Apache was used installed defaults, i.e., no tuning done
    1.  Worked directly on /var/www/html with owner set to me
    1.  Apache "home" page displayed and some, but not all, pages displayed
        1.   As pages from previous boot could be displayed, believe Apache had to be configured to accept new files dynamically or Apache had to be restarted after each change
            1.  Too much work to configure Apache so fell back to a Xampp install on Windows 10
#Windows 10
1. Xaxmpp installed with *only* Apache and MySQL
    1.  Default web root C:\xampp\htdocs
1. XAMPP does not install Windows CLI PHP though it is needed to run setup.php
    1.  As setup.php is only run once, installed Windows Unix Subsystem PHP as install is a known process
        1.  PHP install: `sudo apt-get install php libapache2-mod-php php-mysql`
    1.  Or access PHP from Windows CLI through `\xampp\php\php.exe`
1.  `php setup.php
    PHP Fatal error:  Uncaught Exception: Curl extension is required for TwilioRestClient to work in /mnt/c/xampp/htdocs/opencrisisline/twilio.php:34
    Stack trace:
    /mnt/c/xampp/htdocs/opencrisisline/config.php(45): require()
    /mnt/c/xampp/htdocs/opencrisisline/setup.php(12): include('/mnt/c/xampp/ht...')
    {main}
      thrown in /mnt/c/xampp/htdocs/opencrisisline/twilio.php on line 34`
    1.  Addressed with `sudo apt-get install php-curl`
1.  `PHP Fatal error:  Uncaught Error: Call to undefined function simplexml_load_string() in /mnt/c/xampp/htdocs/opencrisisline/twilio.php:63
i    Stack trace:
    0 /mnt/c/xampp/htdocs/opencrisisline/twilio.php(180): TwilioRestResponse->__construct('https://api.twi...', '<?xml version='...', 404)
    1 /mnt/c/xampp/htdocs/opencrisisline/setup.php(81): TwilioRestClient->request('/2010-04-01/Acc...', 'POST', Array)
    2 {main}
      thrown in /mnt/c/xampp/htdocs/opencrisisline/twilio.php on line 63`
    1. Addressed with `sudo apt-get install php-simplexml`

##Development Notes
xampp/lammp was sufficient for preliminary testing however Twilio REST protocols required access into system hence I used the AWS instance
    



