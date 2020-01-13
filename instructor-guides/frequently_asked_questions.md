# Terraform Workshops FAQ
### Frequently Asked Questions

**Q. How do credentials get handled? Does anyone clean up these resources when the workshop is over?**

A. For AWS and GCP workshops Instruqt provides an entire account or project for each student. Cleanup is done by Instruqt when the track expires or the student clicks the Stop button. On Azure, we utilize temporary credentials fetched from the CAM vault server. Automated cleanup is done by the "Dalek" bot that sweeps through every weekend. You can always encourage your participants to run `terraform destroy` at the end of a workshop to help reduce costs.

**Q. What happens if I get stuck or find errors during a workshop?**

A. You can always post in #se-workshops or #proj-instruqt and someone should be able to assist.

**Q. How do I upgrade my users organizations to trials?**

A. There is another slack channel called #team-se-trial-rqsts where you can ask an admin to upgrade your orgs to trials. We should have self-enabled trials available soon, this will get much easier then.

**Q. In the TF Cloud for AWS workshop sometimes the hashicat app URL doesn't load the first time I run `terraform apply`?**

A. This is because we are using a null provisioner to deploy the app, so sometimes the ec2 instance won't match what's currently in the state file on the first run. Running a second `terraform apply` will fix it for all subsequent runs until you destroy.

**Q. What is the Hashicat application?  How does it work?**

A. The hashicat-aws and hashicat-azure applications are essentially a web server with a webpage that the user can tweak using Terraform variables. The terraform code uses a null provisioner with a random ID to ensure that provisioners run every time you do a `terraform apply`. This allows the students to do a lot of terraform runs without having to tear down and rebuild everything every time. Explain to your students that this custom code is designed for a good training experience, but in the real world the provisioner only runs the first time you do a `terraform apply`.

**Q. Some of my students are rushing ahead in the lab exercises. How can I get them to stay with the class?**

A. You can share the Terraform puzzles git repo with them, and suggest that they work on those when they finish each section. These bite-sized Terraform challenges can be done without disrupting the main lab exercises: https://github.com/hashicorp/workshop-puzzles

**Q. My student somehow got their workstation completely stuck and are unable to get past the check script in Instruqt. Help?**

A. Instructors may now override any check script by creating a file at /tmp/skip-check on the student workstation. This file will override the check and allow you to skip to the next lab challenge. Use with discretion.

**Q. Is there a way to fast-forward to a particular part of a track?**

A. Currently this is only possible for the authors of the track. However, you can use the `/tmp/skip-check` file as mentioned in the previous question to quickly skip past challenges to a particular point in a track. `/tmp/skip-check` must be created for each challenge that you want to skip.