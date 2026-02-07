





<img width="1900" height="955" alt="spray" src="https://github.com/user-attachments/assets/0b9ea52d-b274-42a4-8a84-7a88c67e83ee" />
Microsoft Entra ID Sign-In Investigation & Credential Abuse Analysis
Overview

This lab focused on investigating authentication activity in Microsoft Entra ID to identify suspicious sign-in behavior and distinguish false positives from true security risks. The objective was to simulate realistic SOC scenarios involving repeated authentication failures, successful sign-ins following failures, and identity-based attack patterns such as brute force and password spraying.

Rather than focusing on tenant configuration, this lab emphasized investigation, correlation, and decision-making consistent with Tier 1–2 SOC workflows.

Lab Objectives

Generate controlled failed and successful Entra ID sign-ins

Analyze authentication failure patterns and escalation thresholds

Distinguish brute force activity from password spraying behavior

Interpret Entra ID sign-in error codes and authentication context

Evaluate identity-based risk using IP address, location, and timing

Classify alerts as false positives or true positives using SOC logic

Environment

Microsoft Entra ID (Free Tier)

Azure Portal

Multiple Entra ID user accounts

Browser-based authentication attempts

Internal and external sign-in telemetry

Attack Simulation

Authentication activity was intentionally generated using test Entra ID users. Failed sign-ins were performed using incorrect credentials in short time windows, followed by successful authentication attempts. Additional users were included to simulate both single-user brute force behavior and multi-user password spray patterns.

All activity was conducted in a controlled lab environment without impacting production systems.

Investigation Process

Sign-in logs were reviewed within Microsoft Entra ID to analyze authentication behavior. Events were filtered by user, status, and time range to identify clusters of failed attempts. Error codes and authentication details were examined to determine failure reasons and validate whether activity resulted from user error or potential credential abuse.

<img width="1821" height="911" alt="failuredetails" src="https://github.com/user-attachments/assets/243f3ebf-9200-4370-aea9-565af0a9eb5f" />


Failed sign-ins were then correlated with subsequent successful authentication events to assess escalation risk. Source IP address, geographic location, and client application details were used to evaluate whether behavior was consistent or anomalous.

Key Findings

Low-frequency authentication failures were initially classified as false positives

Rapid failed sign-ins within short time windows increased alert confidence

Successful sign-ins following repeated failures elevated risk classification

Single-user repeated failures aligned with brute-force behavior

Low-volume failures across multiple users aligned with password spraying

<img width="1900" height="955" alt="spray" src="https://github.com/user-attachments/assets/0b9ea52d-b274-42a4-8a84-7a88c67e83ee" />

Internal IP origin reduced immediate impact but still warranted monitoring

SOC Analysis & Classification

Initial authentication failures were treated as benign user behavior. As event frequency increased and failures were followed by a successful sign-in, the activity transitioned to a true positive requiring investigation. Although no immediate account compromise was confirmed, the pattern justified continued monitoring and identity security review.

This lab demonstrated that not all true positives require incident response, but they do require context-aware judgment.

Skills Demonstrated

Identity-based threat investigation

Microsoft Entra ID sign-in log analysis

Authentication failure and error code interpretation

False positive vs true positive classification

Brute force vs password spray differentiation

SOC-style alert triage and escalation reasoning

Key Takeaways

Authentication failures alone are not inherently malicious

Time-based correlation is critical for accurate alert classification

Successful authentication following failures significantly increases risk

Identity telemetry is a core component of modern SOC operations

Context matters more than alert volume

Notes

All authentication events and IP addresses originated from an isolated lab environment. No real users or production systems were involved.
