# cloudwatch-metrix

installing cloudwatch agent 

sudo yum install -y amazon-cloudwatch-agent

sudo dnf install -y amazon-cloudwatch-agent

cd /opt/aws/amazon-cloudwatch-agent/bin

vi config.json

paste JSON content:

{

  "metrics": {
  
    "metrics_collected": {
    
      "mem": {
      
        "measurement": [
        
          "mem_used_percent"
          
        ],
        
        "metrics_collection_interval": 60
        
      }
      
    },
    
    "append_dimensions": {
    
      "InstanceId": "${aws:InstanceId}"
      
    }
    
  }
  
}

sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s



